```
stop(a::Agent)
stop(a::Agent, msg)
```

Terminates an agent, optionally with an error message to be logged, explaining the reason for termination.

# Examples:

```julia
using Fjage

@agent struct MyAgent
  criticalagent::Union{AgentID,Nothing} = nothing
end

function Fjage.startup(a::MyAgent)
  a.criticalagent = agentforservice("CriticalService")
  a.criticalagent === nothing && return stop(a, "Could not find an agent providing CriticalService")
  @info "MyAgent up and running"
end
```
