The Axle project
================

The idea for this project is to innovate how we can send messages to one another. The project has the goal of developing a client and a network of servers.

### Servers

Imagine a bundle of interconnected servers which are basically append-only databases storing a series of messages--similar to a log. The servers keep in sync and make sure to replicate new messages over the network. So asyncronously it syncs up its entries with all servers until each has the same copy. However it only needs to store the messages from a configuration-defined amount of time until it can be deleted, and it should be enough time to keep relevant data available long enough for someone who has been offline to get back on and access it. 

### Clients

The clients would obviously connect to a server on the network. Clients post messages to the server encrypted with the target's public key. Once the messages are propogated, the users which match the routing information then have the ability to receive the messages. Messages have pop semantics in that once a client connects to a server, messages created after the last updated timestamp are downloaded and can be opened.

### Targets

Targets on the network can be specific users or groups of users. Groups of users have access to the private keys created for the group. Single users of course have access to their own private keys.

### Messages

Messages contain information such as:

* Message creation timestamp
* Server name user is connected to
* Their own routing information
* The intended recipient's routing information
* Message data consisting of a mime-type and contents.

This means messages aren't limited to plain text. It could be HTML, speech in audio format, videos, pdfs, etc.


Building
--------

To build, type `make`. You need:

* The [Protocol Buffer](https://developers.google.com/protocol-buffers/) package from Google downloaded and installed.
