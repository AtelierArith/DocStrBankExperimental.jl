```
iers_rot3_itrf_to_gtod(tt_s::Number, m::IERSModel=iers2010b)
```

国際地球参照フレーム（ITRF）からグリニッジ真の日時（GTOD）への回転行列を、`tt_s`の時刻において計算します。これは、`J2000`からのTT秒で表現されます。

!!! note
    [`CPNd`](@ref)モデルは、極運動の影響を無視するため、単位行列を返します。 # TODO: 大きさを指定してください！


!!! note
    [`iers1996`](@ref)モデルでは、GTODとPEF軸は等しいです。なぜなら、IERS 1996年の規約はTIOロケータの影響を考慮していないからです。


## 参照

[`iers_rot3_itrf_to_pef`](@ref)および[`iers_rot3_gcrf_to_gtod`](@ref)も参照してください。
