```
iers_rot3_gcrf_to_gtod(tt_s::Number, m::IERSModel=iers2010b)
```

ジオセントリック天体基準フレーム (GCRF) からグリニッジ真の日時 (GTOD) への回転行列を、`tt_s` の時刻において計算します。これは、`J2000` からのTT秒で表現されています。

!!! note
    [`iers1996`](@ref) の規則が使用される場合、回転は実際にはGCRFではなくMEME2000から計算されます。


!!! note
    EOP摂動補正は、[`iers2003a`](@ref) および [`iers2010a`](@ref) モデルにのみ使用されます。


## 参照

[`iers_rot3_itrf_to_gtod`](@ref) も参照してください。
