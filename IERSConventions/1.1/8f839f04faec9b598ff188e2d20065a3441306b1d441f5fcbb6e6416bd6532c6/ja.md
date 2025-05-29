```
iers_rot3_gcrf_to_tirf(tt_s::Number, m::IERSModel=iers2010b)
```

地心天体基準系 (GCRF) から地球中間基準系 (TIRF) への回転行列を、IERS 規約 `m` に従い、`J2000` からの TT 秒で表現された時刻 `tt_s` において計算します。

!!! note
    CIP 座標 (δX, δY) に対する EOP 補正は、[`iers2003a`](@ref) および [`iers2010a`](@ref) モデルでのみ追加されます。


### 参考文献

  * IERS 技術ノート No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### 参照

[`iers_rot3_gcrf_to_cirf`](@ref) および [`iers_rot3_gcrf_to_itrf`](@ref) も参照してください。
