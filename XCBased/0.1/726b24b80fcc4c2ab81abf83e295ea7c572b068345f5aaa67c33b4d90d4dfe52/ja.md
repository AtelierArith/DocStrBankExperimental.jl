```
wait_for_event(conn:: XCBConnection) -> (XCBEvent, Bool)
```

サーバーからイベントが到着するまでブロックします。イベントと、それがSendEventリクエストを使用して送信されたかどうかを返します。
