```
partial_property(model::EoSModel, p, T, z, property::X; phase=:unknown, threaded=true, vol0=nothing) where {X}
```

指定された温度、圧力、モル量、および関心のある広がりの特性における混合物の部分モル特性を計算します。等式 `sum(z .* partial_property(model,p,T,z,property) - property(model,p,T,z))` が成り立つべきです。

キーワード `phase`、`threaded` および `vol0` は [`Clapeyron.volume`](@ref) ソルバーに渡されます。
