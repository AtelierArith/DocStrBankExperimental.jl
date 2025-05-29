```
poll_for_event(conn:: XCBConnection) -> Union{(XCBEvent, Bool), Nothing}
```

受信したイベントのキューからイベントをポップします。イベントと、それが SendEvent リクエストを使用して送信されたかどうかを返します。キューにイベントがない場合は `nothing` を返します。
