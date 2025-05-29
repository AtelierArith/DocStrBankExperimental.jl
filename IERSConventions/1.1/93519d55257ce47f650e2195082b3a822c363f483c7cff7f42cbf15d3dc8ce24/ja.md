```
iers_rot3_gcrf_to_mod(tt_s::Number, m::IERSModel=iers2010b)
```

ジオセントリック天体参照フレーム (GCRF) から日付平均 (MOD) への回転行列を、`tt_s` の時刻において計算します。これは `J2000` からのTT秒で表現されます。

!!! note
    日付平均軸は、フレームバイアスと歳差行列を適用することによって得られます。このため、[`iers1996`](@ref) の規則が使用される場合、回転は実際にはGCRFではなくMEME2000から計算されます。


### 参照

[`iers_pb`](@ref) および [`iers_rot3_itrf_to_mod`](@ref) も参照してください。
