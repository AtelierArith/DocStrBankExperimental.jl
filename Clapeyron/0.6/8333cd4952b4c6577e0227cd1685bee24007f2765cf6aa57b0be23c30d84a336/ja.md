```
Tproperty(model::EoSModel,p,prop,z::AbstractVector,property = enthalpy;rootsolver = Roots.Order0(),phase =:unknown,abstol = 1e-15,reltol = 1e-15, verbose = false)
```

与えられた `p` と `property` を介して計算された他の任意のバルク特性 `prop` に対して、`property(model,p,T,z,phase) = prop` となる必要な温度 `T` を返します。

すべての圧力のケースが機能するわけではなく、`Clapeyron.bubble_temperature(model,p,z)` および `Clapeyron.dew_temperature(model,p,z)` は常に正しい出発点を見つけるわけではありません。
