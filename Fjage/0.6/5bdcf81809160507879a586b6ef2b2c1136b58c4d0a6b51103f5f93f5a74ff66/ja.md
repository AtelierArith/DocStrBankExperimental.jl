```
request(a::Agent, msg::Message)
request(a::Agent, msg::Message, timeout::Int)
```

リクエストを送信し、応答を待ちます。タイムアウトが指定されている場合、呼び出しは最大で `timeout` ミリ秒ブロックされます。タイムアウトが指定されていない場合は、システムのデフォルトが使用されます。応答メッセージを返すか、応答が受信されなかった場合は `nothing` を返します。
