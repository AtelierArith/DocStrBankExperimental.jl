```
agentsforservice(c::Container, svc::String, owner::Agent)
```

サービス `svc` を提供しているすべてのエージェントを検索し、`owner` が所有する `AgentID` のリストを返します。指定されたサービスを提供しているエージェントが見つからない場合は、空のリストを返します。
