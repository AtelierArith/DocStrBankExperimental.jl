```
agentforservice(a::Agent, svc::String)
```

Find an agent providing a specified service. Returns an owned `AgentID` for the service provider, if one is found, `nothing` otherwise.
