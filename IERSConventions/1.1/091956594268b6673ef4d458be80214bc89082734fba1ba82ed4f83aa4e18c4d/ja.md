```
iers_rot3_itrf_to_cirf(tt_s::Number, m::IERSModel=iers2010b)
```

国際地球参照フレーム（ITRF）から天体中間参照フレーム（CIRF）への回転行列を、`tt_s` の時刻において計算します。これは、`J2000` からのTT秒で表現され、IERSの規約 `m` に従います。

!!! note
    極運動は [`CPNd`](@ref) モデルでは無視されます。


### 参考文献

  * IERS技術ノート No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### 参照

[`iers_rot3_gcrf_to_cirf`](@ref) および [`iers_rot3_itrf_to_tirf`](@ref) も参照してください。
