```
entropy(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

デフォルト単位: `[J/K]`

エントロピーを計算します。エントロピーは次のように定義されます:

```julia
S = -∂A/∂T
```

内部的には、[`Clapeyron.volume`](@ref)を呼び出して`V`を取得し、`VT_entropy(model,V,T,z)`を介してプロパティを計算します。

キーワード`phase`、`threaded`、および`vol0`は、[`Clapeyron.volume`](@ref)ソルバーに渡されます。
