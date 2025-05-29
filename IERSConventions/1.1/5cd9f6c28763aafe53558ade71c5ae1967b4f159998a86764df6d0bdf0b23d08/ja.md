```
iers_rot6_gcrf_to_itrf(tt_s::Number, m::IERSModel=iers2010b)
```

地心天体基準系 (GCRF) から国際地球基準系 (ITRF) への回転行列とその導関数を、IERS 規約 `m` に従い、`J2000` からの TT 秒で表現された時刻 `tt_s` で計算します。

!!! note
    CIP 座標 (δX, δY) への EOP 補正は、[`iers2003a`](@ref) および [`iers2010a`](@ref) モデルでのみ追加されます。


!!! note
    [`CPNd`](@ref) モデルでは極運動は無視されます。


!!! note
    振動と歳差効果の時間導関数は無視されます。


### 参考文献

  * IERS 技術ノート No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)
