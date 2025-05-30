```
create_simulation_container(start_time::DateTime; communication_sim::Union{Nothing,CommunicationSimulation}=nothing, task_sim::Union{Nothing,TaskSimulation}=nothing)
```

シミュレーションコンテナを作成します。コンテナは `start_time` で初期化されます。

デフォルトでは、通信シミュレーションには [`SimpleCommunicationSimulation`](@ref) が使用され、エージェントのタスクをシミュレートするためには [`SimpleTaskSimulation`](@ref) が使用されます。これらを置き換えるために、`communication_sim` およびそれぞれ `task_sim` を設定できます。
