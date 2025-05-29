```
enthalpy(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

デフォルト単位: `[J]`

エンタルピーを計算します。エンタルピーは次のように定義されます:

```julia
H = A - T * ∂A/∂T - V * ∂A/∂V
```

内部的には、[`Clapeyron.volume`](@ref)を呼び出して`V`を取得し、`VT_enthalpy(model,V,T,z)`を介してプロパティを計算します。

キーワード`phase`、`threaded`、および`vol0`は、[`Clapeyron.volume`](@ref)ソルバーに渡されます。
