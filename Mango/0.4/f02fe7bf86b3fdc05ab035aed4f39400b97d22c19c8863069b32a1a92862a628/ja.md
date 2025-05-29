```
init(protocol::MQTTProtocol, stop_check::Function, data_handler::Function)
```

提供された `protocol` のために Mosquitto ループタスクを初期化し、受信したメッセージを `data_handler` に転送します。
