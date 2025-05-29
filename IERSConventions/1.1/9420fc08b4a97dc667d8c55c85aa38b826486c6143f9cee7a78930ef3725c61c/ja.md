```
iers_rot3_gcrf_to_tod(tt_s::Number, m::IERSModel=iers2010b)
```

地心天体基準系 (GCRF) から日付の真の方向 (TOD) への回転行列を、`tt_s` の時刻において、J2000 からの TT 秒で表現します。

!!! note
    日付の真の方向の軸は、フレームバイアス、歳差、そして歳差行列を適用することによって得られます。このため、[`iers1996`](@ref) の規則が使用される場合、回転は実際には GCRF ではなく MEME2000 から始まることになります。


!!! note
    EOP の歳差補正は、[`iers2003a`](@ref) および [`iers2010a`](@ref) モデルにのみ使用されます。


## 参照

[`iers_npb`](@ref) および [`iers_rot3_itrf_to_tod`](@ref) も参照してください。
