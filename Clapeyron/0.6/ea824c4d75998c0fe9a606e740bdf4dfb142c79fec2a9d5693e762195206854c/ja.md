```
internal_energy_res(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

デフォルト単位: `[J]`

残余内部エネルギーを計算します。これは次のように定義されます:

```julia
U = Ar - T * ∂Ar/∂T
```

内部的には、[`Clapeyron.volume`](@ref)を呼び出して`V`を取得し、`VT_internal_energy_res(model,V,T,z)`を介してプロパティを計算します。

キーワード`phase`、`threaded`、および`vol0`は、[`Clapeyron.volume`](@ref)ソルバーに渡されます。
