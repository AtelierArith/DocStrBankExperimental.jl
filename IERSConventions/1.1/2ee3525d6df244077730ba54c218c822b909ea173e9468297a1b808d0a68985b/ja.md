```
iers_rot3_gcrf_to_pef(tt_s::Number, m::IERSModel=iers2010b)
```

地心天体参照フレーム (GCRF) から擬似地球固定 (PEF) への回転行列を、`tt_s` の時刻において計算します。`J2000` からのTT秒で表現されています。

!!! note
    [`iers1996`](@ref) 規則が使用されている場合、回転は実際にはGCRFではなくMEME2000から計算されます。


!!! note
    EOP摂動補正は、[`iers2003a`](@ref) および [`iers2010a`](@ref) モデルにのみ使用されます。


!!! note
    [`iers1996`](@ref) および [`CPNd`](@ref) モデルの場合、PEFとGTOD軸の間に違いはありません。 # TODO: 回転の大きさを指定してください！


## 参照

[`iers_rot3_gcrf_to_gtod`](@ref) および [`iers_rot3_itrf_to_pef`](@ref) も参照してください。
