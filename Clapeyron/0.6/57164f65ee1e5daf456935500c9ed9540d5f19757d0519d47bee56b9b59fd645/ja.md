```
helmholtz_free_energy(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
helmholtz_energy(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

デフォルト単位: `[J]`

ヘルムホルツ自由エネルギーを計算します。定義は次の通りです:

```julia
A = eos(model,V(p),T,z)
```

内部的には、[`Clapeyron.volume`](@ref)を呼び出して`V`を取得し、`VT_helmholtz_free_energy(model,V,T,z)`を介してプロパティを計算します。

キーワード`phase`、`threaded`、および`vol0`は、[`Clapeyron.volume`](@ref)ソルバーに渡されます。
