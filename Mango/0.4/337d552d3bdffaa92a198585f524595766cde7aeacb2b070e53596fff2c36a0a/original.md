```
send(protocol::Protocol{T}, destination::T, message::Any) where {T}
```

Send the message `message` to the agent known by the adress `destination`. How the message is exactly handled is  determined by the protocol invoked. 

The type of the destination has to match with the protocol. The function returns a boolean indicating  whether the message was successfull sent
