```
iers_rot3_itrf_to_mod(tt_s::Number, m::IERSModel=iers2010b)
```

国際地球参照フレーム (ITRF) から日付平均 (MOD) への回転行列を、`tt_s` の時刻において計算します。これは `J2000` からのTT秒で表現されます。

!!! note
    EOP摂動補正は、[`iers2003a`](@ref) および [`iers2010a`](@ref) モデルにのみ使用されます。


## 参照

[`iers_rot3_itrf_to_tod`](@ref) および [`iers_rot3_gcrf_to_mod`](@ref) も参照してください。
