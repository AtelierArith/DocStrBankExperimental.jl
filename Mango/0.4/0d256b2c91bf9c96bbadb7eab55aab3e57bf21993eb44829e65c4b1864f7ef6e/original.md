Type for all implementations of protocols, acts like an interface. A protocol defines the way message are processed and especially sent and received  to an other peer. F.E. A protocol could be to send messages using a plain TCP connection, which would indicate that an internet address (host + port) is required for the communication.

The parameterized type T indicates type, which defines the address data of the receiver and sender.

Every protocol has to define two methods.

1. send: defines the behavior of the protocol when an agents sends a messages
2. init: defines the necessary steps to initialize (especially) the receiver loop and

```
	 therefore accepts a stop check and a data handler function to indicate when the receiver should stop, 
	 respectively how to dispatch the received message to the correct agent
```
