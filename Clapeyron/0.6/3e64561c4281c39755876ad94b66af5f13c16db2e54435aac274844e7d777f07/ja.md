```
aqueous_activity(model::EoSModel,p,T,z=SA[1.0]; phase=:unknown, threaded=true, vol0=nothing)
```

水中の無限希釈を基準とした活量を計算します。これは次のように定義されます：

```julia
log(a) = (μ_mixt - μ_inf) / R̄ / T
```

ここで、`μ_mixt`は混合物の化学ポテンシャルであり、`μ_inf`は水中の無限希釈における成分の化学ポテンシャルです。

内部的には、[`Clapeyron.volume`](@ref)を呼び出して`V`を取得し、`VT_fugacity_coefficient(model,V,T,z)`を介して特性を計算します。

キーワード`phase`、`threaded`、および`vol0`は、[`Clapeyron.volume`](@ref)ソルバーに渡されます。
