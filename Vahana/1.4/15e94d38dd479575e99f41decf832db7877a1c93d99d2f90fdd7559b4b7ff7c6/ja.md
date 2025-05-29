```
add_agent!(sim, agent::T)::AgentID
```

シミュレーション `sim` にタイプ T のエージェントを1つ追加します。

T は、[`register_agenttype!`](@ref) を呼び出すことで事前に登録されている必要があります。

`add_agent!` は新しい AgentID を返します。この ID は、[`finish_init!`](@ref) が呼び出されるまで（`add_agent!` が初期化フェーズで呼び出された場合）、または遷移関数が終了するまで（`add_agent!` が [`apply!`](@ref) コールバックで呼び出された場合）このエージェントからまたはこのエージェントへのエッジを作成するために使用できます。他の目的で ID を使用しないでください。安定していることは保証されていません。

他にも [`add_agents!`](@ref)、[`add_edge!`](@ref)、および [`add_edges!`](@ref) を参照してください。
