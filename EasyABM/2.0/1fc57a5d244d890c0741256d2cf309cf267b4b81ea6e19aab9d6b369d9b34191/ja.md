```julia
grid_3d_agents(
    n::Int64;
    pos,
    space_type,
    agent_type,
    kwargs...
) -> Vector{EasyABM.Agent3D{Int64, EasyABM.PeriodicType, EasyABM.StaticType}}

```

n個の2dエージェントのリストを、キーワード引数として指定されたプロパティを持って作成します。
