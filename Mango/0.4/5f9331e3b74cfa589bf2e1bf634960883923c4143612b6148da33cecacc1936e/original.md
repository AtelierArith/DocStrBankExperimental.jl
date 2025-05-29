```
init(protocol::Protocol{T}, stop_check::Function, data_handler::Function) where {T}
```

Initialized the protocols internal loops (if exists). In most implementation this would mean that the receiver loop is started. To handle received messages the `data_handler` function can be passed `(msg, sender) -> your handling code`. 

To control the lifetime of the loops a stop_check should be passed (() -> boolean). If the stop check is true the loops will  terminate. The exact behavior depends on the implementation though.
