```
iers_rot3_itrf_to_tirf(tt_s::Number, m::IERSModel=iers2010b)
```

国際地球参照フレーム（ITRF）から地球中間参照フレーム（TIRF）への回転行列を、IERSの規約 `m` に従い、`J2000` からのTT秒で表現された時刻 `tt_s` において計算します。

!!! note
    極運動は [`CPNd`](@ref) モデルでは無視されます。


### 参考文献

  * IERS技術ノート No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### 参照

[`iers_rot3_gcrf_to_tirf`](@ref) および [`iers_rot3_itrf_to_cirf`](@ref) も参照してください。
