```
mass_density(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true)
```

デフォルト単位: `[kg/m^3]`

質量密度を計算します。質量密度は次のように定義されます：

```julia
ρₙ = Mr/V
```

ここで `Mr` は入力組成におけるモデルの分子量です。

内部的には、[`Clapeyron.volume`](@ref) を呼び出して `V` を取得し、`VT_mass_density(model,V,T,z)` を介してプロパティを計算します。

キーワード `phase`、`threaded` および `vol0` は [`Clapeyron.volume`](@ref) ソルバーに渡されます。
