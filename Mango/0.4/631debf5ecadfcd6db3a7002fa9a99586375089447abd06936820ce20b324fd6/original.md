```
delete_forwarding_rule(agent, from_addr::AgentAddress, to_address::Union{Nothing,AgentAddress})
```

Delete an added forwarding rule. If `to_address` is not set, all rules are removed matching `from_addr`. If it set, both addresses need to match.
