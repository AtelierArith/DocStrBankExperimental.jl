```
realtime_milliseconds(t::AbstractArray{<:TimeType}, T = Float64)
```

[`realtime_days`](@ref)と似ていますが、今回は測定単位がミリ秒です。追加の精度のために、`t`の直接の差分が使用されます。
