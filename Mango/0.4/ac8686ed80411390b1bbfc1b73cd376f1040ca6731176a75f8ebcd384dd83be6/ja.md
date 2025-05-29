```
add_forwarding_rule(agent, from_addr::AgentAddress, to_address::AgentAddress, forward_replies::Bool)
```

メッセージ転送のルールを追加します。

エージェントを呼び出すと、`from_addr`から来るすべてのメッセージが`to_address`に自動転送されます。`forward_replies`が設定されている場合、`to_address`からのすべての返信が`from_addr`に転送されます。
