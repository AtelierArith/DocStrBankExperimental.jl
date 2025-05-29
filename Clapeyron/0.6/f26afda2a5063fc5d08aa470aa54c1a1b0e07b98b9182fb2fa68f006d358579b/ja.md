```
AntoineSaturation <: SaturationMethod
AntoineSaturation(;T0 = nothing,
                    vl = nothing,
                    vv = nothing,
                    f_limit = 0.0,
                    atol = 1e-8,
                    rtol = 1e-12,
                    max_iters = 10^4,
                    crit = nothing,
                    crit_retry = false)
```

`saturation_temperature` のための飽和法。Clapeyron 0.3.7 からの飽和温度のデフォルトメソッドです。飽和条件のための体積-温度方程式系を解きます。

`T0` のみが提供される場合、`vl` と `vv` は [`x0_sat_pure`](@ref) を介して取得されます。`T0` が提供されない場合、[`x0_saturation_temperature`](@ref) を介して取得されます。デフォルトのスタート地点は [`crit_pure`](@ref) を呼び出すため、`x0_saturation_temperature` をオーバーロードすることをお勧めします。これにより、理想的な時間よりも遅くなります。`f_limit`、`atol`、`rtol`、`max_iters` は非線形システムソルバーに渡されます。
