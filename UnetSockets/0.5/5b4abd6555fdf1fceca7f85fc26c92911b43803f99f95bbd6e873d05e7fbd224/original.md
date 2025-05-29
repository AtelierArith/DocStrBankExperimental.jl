Receives a datagram sent to the local node and the bound protocol number. If the socket is unbound, then datagrams with all unreserved protocols are received. Any broadcast datagrams are also received.

This call blocks until a datagram is available, the socket timeout is reached, or until cancel() is called.
