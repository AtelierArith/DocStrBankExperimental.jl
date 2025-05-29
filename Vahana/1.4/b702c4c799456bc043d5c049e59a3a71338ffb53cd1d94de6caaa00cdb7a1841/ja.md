```
num_agents(sim, ::Type{T}, [all_ranks=true])
```

`all_ranks`が`true`の場合、この関数はシミュレーション`sim`のタイプTのエージェントの数を取得します。`false`に設定されている場合、関数はプロセスによって管理されているエージェントの数を返します。

関連情報として[`add_agents!`]および[`all_agents`](@ref)を参照してください。
