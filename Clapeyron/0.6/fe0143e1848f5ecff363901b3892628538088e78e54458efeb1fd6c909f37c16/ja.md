```
ChemPotVSaturation <: SaturationMethod
ChemPotVSaturation(V0)
ChemPotVSaturation(;vl = nothing,
                    vv = nothing,
                    crit = nothing,
                    crit_retry = true
                    f_limit = 0.0,
                    atol = 1e-8,
                    rtol = 1e-12,
                    max_iters = 10^4)
```

デフォルトの`saturation_pressure`は、`Clapeyron.jl`で使用される飽和法です。これは、体積基準での化学ポテンシャルの等式を使用します。体積が提供されていない場合、[`x0_sat_pure`](@ref)を使用します。これらの初期推定が失敗し、指定が臨界点に近い場合、対応状態を使用してもう一度試みます。`crit_retry`がtrueの場合、初期解決が失敗した場合、臨界点を計算することでより良い推定を得ようとします。`f_limit`、`atol`、`rtol`、`max_iters`は非線形システムソルバーに渡されます。
