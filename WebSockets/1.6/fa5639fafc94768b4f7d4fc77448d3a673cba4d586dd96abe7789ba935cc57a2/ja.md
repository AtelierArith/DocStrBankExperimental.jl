```
read(ws::WebSocket)
```

典型的な使用法:     msg = String(read(ws)) WebSocketから1つの非制御メッセージを読み取ります。読み取られた制御メッセージはhandle*control*frame関数によって処理されます。メッセージのデータ（内容/ボディ/ペイロード）だけがVector{UInt8}として返されます。

この関数は、完全な非制御メッセージが読み取られるまで戻りません。
