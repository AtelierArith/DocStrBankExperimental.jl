```
gibbs_free_energy_res(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
gibbs_energy_res(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

デフォルト単位: `[J]`

残余ギブズ自由エネルギーを計算します。これは次のように定義されます:

```julia
G = Ar - V*∂Ar/∂V
```

内部的には、[`Clapeyron.volume`](@ref)を呼び出して`V`を取得し、`VT_gibbs_free_energy_res(model,V,T,z)`を介してプロパティを計算します。

キーワード`phase`、`threaded`、および`vol0`は、[`Clapeyron.volume`](@ref)ソルバーに渡されます。
