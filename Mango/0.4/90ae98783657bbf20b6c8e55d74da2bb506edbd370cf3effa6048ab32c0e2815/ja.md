```
reply_to(
agent::AgentInterface,
content::Any,
received_meta::AbstractDict,
```

)

受信したメッセージに対してエージェントが受け取ったメタデータを使用して返信するための便利なメソッドです。これにより、通常の `send_message` を `reply_to(agent, "Pong", meta)` に簡略化できます。具体的には、`send_message(agent, "Pong", AgentAddress(aid=meta["sender_id"], address=meta["sender_addr"]))` を短縮します。

さらに、エージェントアドレス（トラッキングIDを含む、アドレスの一部です！）が正しくマンゴーコンテナに渡されることを保証します。
