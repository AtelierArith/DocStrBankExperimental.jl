```
add_forwarding_rule(agent, from_addr::AgentAddress, to_address::AgentAddress, forward_replies::Bool)
```

Add a rule for message forwarding.

After calling the agent will auto-forward every message coming from `from_addr` to `to_address`. If forward*replies is set, all replies from `to*address`are forwarded back to`from_addr`.
