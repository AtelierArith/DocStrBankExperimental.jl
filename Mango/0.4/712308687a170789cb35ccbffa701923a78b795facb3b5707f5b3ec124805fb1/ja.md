```
init(protocol::TCPProtocol, stop_check::Function, data_handler::Function)
```

tcpプロトコルを初期化しました。これにより、受信者と停止ループが開始されます。受信者ループは、すべての受信メッセージに対してdata_handlerを呼び出します。さらに、送信者アドレスとしてInetAddrオブジェクトを提供します。
