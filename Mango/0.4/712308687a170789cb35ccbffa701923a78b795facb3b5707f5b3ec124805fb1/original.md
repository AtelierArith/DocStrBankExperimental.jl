```
init(protocol::TCPProtocol, stop_check::Function, data_handler::Function)
```

Initialized the tcp protocol. This starts the receiver and stop loop. The receiver loop will call the data_handler with every incoming message. Further it provides as sender adress a InetAddr object. 
