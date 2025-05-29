```
molar_density(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

デフォルト単位: `[mol/m^3]`

モル密度を計算します。モル密度は次のように定義されます:

```julia
ρₙ = ∑nᵢ/V
```

内部的には、[`Clapeyron.volume`](@ref)を呼び出して`V`を取得し、`VT_molar_density(model,V,T,z)`を介してプロパティを計算します。

キーワード`phase`、`threaded`、および`vol0`は、[`Clapeyron.volume`](@ref)ソルバーに渡されます。
