```
reply_to(
agent::AgentInterface,
content::Any,
received_meta::AbstractDict,
```

)

受信したメッセージに対して、エージェントが受け取ったメタデータを使用して返信するための便利なメソッドです。これにより、通常の `send_message` を `send_message(agent, "Pong", AgentAddress(aid=meta["sender_id"], address=meta["sender_addr"]))` から `reply_to(agent, "Pong", meta)` に簡略化できます。

さらに、エージェントアドレス（トラッキングIDを含む、アドレスの一部です！）がマンゴーコンテナに正しく渡されることを保証します。
