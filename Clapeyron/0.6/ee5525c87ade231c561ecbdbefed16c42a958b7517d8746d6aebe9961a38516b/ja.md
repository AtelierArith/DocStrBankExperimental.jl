```
ChemPotDensitySaturation <: SaturationMethod
ChemPotDensitySaturation(;vl = nothing,
                        vv = nothing,
                        crit = nothing,
                        f_limit = 0.0,
                        atol = 1e-8,
                        rtol = 1e-12,
                        max_iters = 10^4)
```

`saturation_pressure`のための飽和法です。これは、密度基準での化学ポテンシャルの等価性を使用します。ボリュームが提供されていない場合、[`x0_sat_pure`](@ref)を使用します。`vl`と`vv`は、液体と蒸気のボリュームの初期推定値です。`f_limit`、`atol`、`rtol`、`max_iters`は非線形システムソルバーに渡されます。
