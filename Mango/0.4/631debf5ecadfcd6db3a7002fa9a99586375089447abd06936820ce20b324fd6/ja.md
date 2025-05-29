```
delete_forwarding_rule(agent, from_addr::AgentAddress, to_address::Union{Nothing,AgentAddress})
```

追加された転送ルールを削除します。`to_address`が設定されていない場合、`from_addr`に一致するすべてのルールが削除されます。設定されている場合、両方のアドレスが一致する必要があります。
