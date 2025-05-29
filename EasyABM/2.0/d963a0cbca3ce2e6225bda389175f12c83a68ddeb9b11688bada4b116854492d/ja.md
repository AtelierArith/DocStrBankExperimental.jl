```julia
con_3d_agents(
    n::Int64;
    pos,
    space_type,
    agent_type,
    kwargs...
) -> Vector{EasyABM.Agent3D{Float64, EasyABM.PeriodicType, EasyABM.StaticType}}

```

n個の3Dエージェントのリストを、キーワード引数として指定されたプロパティで作成します。
