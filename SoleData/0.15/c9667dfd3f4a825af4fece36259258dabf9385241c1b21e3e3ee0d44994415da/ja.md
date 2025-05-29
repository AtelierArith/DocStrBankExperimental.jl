```
struct ExplicitModalLogiset{
    W<:AbstractWorld,
    U,
    FT<:AbstractFeature,
    FR<:AbstractFrame{W},
} <: AbstractModalLogiset{W,U,FT,FR}

    d :: Vector{Tuple{Dict{W,Dict{FT,U}},FR}}

end
```

特徴がブール値であり、各インスタンスが各世界に対して`true`の特徴のセットを関連付けるログセットです。

[`AbstractModalLogiset`](@ref)も参照してください。
