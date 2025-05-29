```
agentforservice(a::Agent, svc::String)
```

指定されたサービスを提供するエージェントを見つけます。サービスプロバイダーが見つかった場合は所有された `AgentID` を返し、見つからなかった場合は `nothing` を返します。
