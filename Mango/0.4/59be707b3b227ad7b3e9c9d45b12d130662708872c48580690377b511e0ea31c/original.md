```
send(protocol::TCPProtocol, destination::InetAddr, message::Vector{UInt8})
```

Send a message `message` over plain TCP using `destination` as destination address. The message has to be provided  as a form, which is writeable to an arbitrary IO-Stream.

Return true if successfull.
