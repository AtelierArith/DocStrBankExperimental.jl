```
UncertainValue(kerneldensity::Type{K}, data::Vector{T};
    kernel::Type{D} = Normal,
    npoints::Int=2048) where {K <: UnivariateKDE, D <: Distribution, T}
```

データに対してカーネル密度推定によって不確実な値を構築します。

カーネル密度推定では高速フーリエ変換が使用されるため、ポイントの数は2の累乗である必要があります（デフォルト = 2048）。
