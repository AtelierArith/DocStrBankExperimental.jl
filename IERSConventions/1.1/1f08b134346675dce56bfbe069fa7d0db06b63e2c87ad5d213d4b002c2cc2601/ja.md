```
iers_rot3_itrf_to_tod(tt_s::Number, m::IERSModel=iers2010b)
```

国際地球基準系 (ITRF) から日時の真の位置 (TOD) への回転行列を、`J2000` からの TT 秒で表された時刻 `tt_s` に対して計算します。

!!! note
    経度の EOP 補正は、[`iers2003a`](@ref) および [`iers2010a`](@ref) モデルにのみ使用されます。


## 参照

[`iers_rot3_itrf_to_gtod`](@ref) および [`iers_rot3_gcrf_to_tod`](@ref) も参照してください。
