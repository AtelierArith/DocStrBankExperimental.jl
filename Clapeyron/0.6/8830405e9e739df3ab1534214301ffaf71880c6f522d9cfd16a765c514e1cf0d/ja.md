```
gibbs_free_energy(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
gibbs_energy(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

デフォルト単位: `[J]`

ギブズ自由エネルギーを計算します。定義は次の通りです:

```julia
G = A + p*V
```

内部的には、[`Clapeyron.volume`](@ref)を呼び出して`V`を取得し、`VT_gibbs_free_energy(model,V,T,z)`を介してプロパティを計算します。

キーワード`phase`、`threaded`、および`vol0`は、[`Clapeyron.volume`](@ref)ソルバーに渡されます。
