```
internal_energy(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

デフォルト単位: `[J]`

内部エネルギーを計算します。内部エネルギーは次のように定義されます:

```julia
U = A - T * ∂A/∂T
```

内部的には、[`Clapeyron.volume`](@ref)を呼び出して`V`を取得し、`VT_internal_energy(model,V,T,z)`を介してプロパティを計算します。

キーワード`phase`、`threaded`、および`vol0`は、[`Clapeyron.volume`](@ref)ソルバーに渡されます。
