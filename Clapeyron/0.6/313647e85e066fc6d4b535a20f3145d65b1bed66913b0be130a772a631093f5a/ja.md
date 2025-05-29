```
adiabatic_index(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

デフォルト単位: `[J/K]`

定義された定圧比熱容量を計算します:

```julia
γ = Cp/Cv
```

内部的には、[`Clapeyron.volume`](@ref)を呼び出して`V`を取得し、`VT_adiabatic_index(model,V,T,z)`を介してプロパティを計算します。

キーワード`phase`、`threaded`、および`vol0`は、[`Clapeyron.volume`](@ref)ソルバーに渡されます。

!!! warning "正確な理想モデルが必要"
    このプロパティは、少なくとも二次の理想モデル温度導関数を必要とします。これらのプロパティを計算している場合は、`BasicIdeal`デフォルト（例: `EoS(["species"];idealmodel = ReidIdeal)`）とは異なる理想モデルを使用することを検討してください。

