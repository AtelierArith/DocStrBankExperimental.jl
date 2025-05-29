```
joule_thomson_coefficient(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

デフォルト単位: `[K/Pa]`

ジュール・トムソン係数を計算します。これは次のように定義されます:

```julia
μⱼₜ = -(∂²A/∂V∂T - ∂²A/∂V² * ((T*∂²A/∂T² + V*∂²A/∂V∂T) / (T*∂²A/∂V∂T + V*∂²A/∂V²)))^-1
```

内部的には、[`Clapeyron.volume`](@ref)を呼び出して`V`を取得し、`VT_joule_thomson_coefficient(model,V,T,z)`を介してプロパティを計算します。

キーワード`phase`、`threaded`、および`vol0`は、[`Clapeyron.volume`](@ref)ソルバーに渡されます。

!!! warning "正確な理想モデルが必要"
    このプロパティは、少なくとも二次の理想モデル温度導関数を必要とします。これらのプロパティを計算している場合は、デフォルトの`BasicIdeal`とは異なる理想モデル（例: `EoS(["species"];idealmodel = ReidIdeal)`）を使用することを検討してください。

