```julia
cartesian2cylinderial(
    p::PhysicalParticles.PVector
) -> Tuple{Any, Any, Number}

```

`PVector`を円筒座標に変換します。タプル(r, θ, z)を返します。
