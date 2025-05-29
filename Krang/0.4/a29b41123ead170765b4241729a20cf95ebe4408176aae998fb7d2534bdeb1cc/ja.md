```julia
penrose_walker(
    metric::Krang.Kerr{T},
    r,
    θ,
    p_u::AbstractVector,
    f_u::AbstractVector
) -> Tuple{Any, Any}

```

流体粒子から放出された運動量 f*u を持つ光子のためのペンローズウォーカ定数を返します。
