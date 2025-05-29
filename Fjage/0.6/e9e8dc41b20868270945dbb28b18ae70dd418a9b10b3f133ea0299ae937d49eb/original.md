```
agentforservice(c::Container, svc::String, owner::Agent)
```

Lookup any agent providing the service `svc`, and return an `AgentID` owned by `owner`. Returns `nothing` if no agent providing specified service found.
