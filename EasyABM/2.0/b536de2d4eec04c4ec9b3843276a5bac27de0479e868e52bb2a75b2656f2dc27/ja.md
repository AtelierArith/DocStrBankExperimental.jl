```julia
grid_2d_agents(
    n::Int64;
    pos,
    space_type,
    agent_type,
    kwargs...
) -> Vector{EasyABM.Agent2D{Int64, EasyABM.PeriodicType, EasyABM.StaticType}}

```

n個の2次元エージェントのリストを、キーワード引数として指定されたプロパティで作成します。
