```
chemical_potential(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

デフォルト単位: `[J/mol]`

化学ポテンシャルを計算します。これは次のように定義されます:

```julia
μᵢ = ∂A/∂nᵢ
```

内部的には、[`Clapeyron.volume`](@ref)を呼び出して`V`を取得し、`VT_chemical_potential(model,V,T,z)`を介してプロパティを計算します。

キーワード`phase`、`threaded`、および`vol0`は、[`Clapeyron.volume`](@ref)ソルバーに渡されます。
