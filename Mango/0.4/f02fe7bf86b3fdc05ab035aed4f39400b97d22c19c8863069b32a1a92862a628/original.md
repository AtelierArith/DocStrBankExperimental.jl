```
init(protocol::MQTTProtocol, stop_check::Function, data_handler::Function)
```

Initialize the Mosquitto looping task for the provided `protocol` and forward incoming messages to `data_handler`. 
