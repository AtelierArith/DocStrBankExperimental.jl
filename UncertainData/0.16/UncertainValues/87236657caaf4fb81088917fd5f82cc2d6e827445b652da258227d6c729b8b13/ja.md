```
UncertainValue(data::Vector{T};
    kernel::Type{D} = Normal,
    npoints::Int=2048) where {D <: Distributions.Distribution, T}
```

データに対してカーネル密度推定を用いて不確実な値を構築します。

カーネル密度推定には高速フーリエ変換が使用されるため、ポイント数は2の累乗である必要があります（デフォルト = 2048）。
