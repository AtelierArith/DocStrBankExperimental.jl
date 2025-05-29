```
close(ws::WebSocket)
close(ws::WebSocket, statusnumber = n)
close(ws::WebSocket, statusnumber = n, freereason = "my reason")
```

OPCODE_CLOSE フレームを送信し、同じ応答を待つか、合理的な時間、10.0 秒が経過するまで待ちます。閉じている間に受信したデータは破棄されます。RFC 6455 7.4.1 に従ったステータス番号 n を含めることができます。詳細は WebSockets.codeDesc を参照してください。
