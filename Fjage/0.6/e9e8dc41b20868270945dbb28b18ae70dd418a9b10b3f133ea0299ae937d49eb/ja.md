```
agentforservice(c::Container, svc::String, owner::Agent)
```

サービス `svc` を提供するエージェントを検索し、`owner` によって所有されている `AgentID` を返します。指定されたサービスを提供するエージェントが見つからない場合は `nothing` を返します。
