```
agent_hierarchy_mmd(a; use_uuid = 0)
```

This function can help display the agent hierarchy for concrete models. It assumes the user wants to pass the results into a Mermaid diagram for easier visualization of concrete model instantiations. The kwarg `use_uuid` will append the last `use_uuid` digits of each agent to their name following an underscore. This can be useful if it is not possible to distinguish unique agents purely by their name alone.

# Examples

```julia
# the following may be pasted into the Mermaid live editor:
# https://mermaid.live/

@aagent FreeAgent struct AgentType1 end
base = FreeAgent("agent1")
entangle!(base, AgentType1("agent2"))
entangle!(base, AgentType1("agent3"))

# do not print UUIDs
hierarchy = agent_hierarchy_mmd(base)
print(join(hierarchy,""))

# print last 4 digits of UUIDs
hierarchy = agent_hierarchy_mmd(base, use_uuid = 4)
print(join(hierarchy,""))
```
