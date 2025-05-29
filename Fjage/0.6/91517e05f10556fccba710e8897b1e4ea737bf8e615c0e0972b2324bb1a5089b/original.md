```
agentsforservice(c::Container, svc::String, owner::Agent)
```

Lookup all agents providing the service `svc`, and return list of `AgentID` owned by `owner`. Returns an empty list if no agent providing specified service found.
