```
 AgentID
```

The AgentID is a combination of different (Vahana internal) information about an agent, like e.g. the position where the agent state is stored. It's important to understand that at different times different agents can have the same agent id, therefore those ids can not be used to identify an agent a simulation run. If you need this, you must add an field to the agent state and create an unique value for this field in the agent constructor by yourself.
