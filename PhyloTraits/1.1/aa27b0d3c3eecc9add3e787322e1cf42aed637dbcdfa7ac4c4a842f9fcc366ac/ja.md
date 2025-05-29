```
shiftathybrids(value::Vector{T} where T<:Real, net::HybridNetwork; checkpreorder::Bool=true)
```

ハイブリッドノードの下にあるすべてのエッジにシフトを持つオブジェクト [`ShiftNet`](@ref) を構築します。値のベクトルは、ネットワーク内のハイブリッドの数と同じ長さでなければなりません。
