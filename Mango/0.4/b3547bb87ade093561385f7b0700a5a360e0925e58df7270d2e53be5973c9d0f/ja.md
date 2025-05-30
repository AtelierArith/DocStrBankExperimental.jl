```
send_message(
agent::AgentInterface,
content::Any,
agent_address::Address;
kwargs...,
```

)

`content`を持つメッセージを`agent_address`で表されるエージェントに送信します。

このメソッドは常にsender_idを設定します。さらに、メッセージの内部メタデータを埋めるために、追加のキーワード引数を定義できます。
