```
stop(a::Agent)
stop(a::Agent, msg)
```

エージェントを終了します。オプションで、終了の理由を説明するエラーメッセージをログに記録します。

# 例:

```julia
using Fjage

@agent struct MyAgent
  criticalagent::Union{AgentID,Nothing} = nothing
end

function Fjage.startup(a::MyAgent)
  a.criticalagent = agentforservice("CriticalService")
  a.criticalagent === nothing && return stop(a, "CriticalServiceを提供するエージェントが見つかりませんでした")
  @info "MyAgentが起動し、稼働中です"
end
```
