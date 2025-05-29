```
iers_rot12_gcrf_to_itrf(tt_s::Number, m::IERSModel=iers2010b)
```

地心天体基準系 (GCRF) から国際地球基準系 (ITRF) への回転行列、その1階、2階、3階導関数を、IERSの規約 `m` に従い、`J2000` からのTT秒で表現された時刻 `tt_s` において計算します。

!!! note
    CIP座標 (δX, δY) へのEOP補正は、[`iers2003a`](@ref) および [`iers2010a`](@ref) モデルでのみ追加されます。


!!! note
    [`CPNd`](@ref) モデルでは極運動は無視されます。


!!! note
    振動と歳差効果の時間導関数は無視されます。


### 参考文献

  * IERS技術ノート No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

```
