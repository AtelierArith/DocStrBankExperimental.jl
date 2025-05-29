```
iers_era_rotm(m::IERSModel, ut1_d::Number)
```

CIRFからTIRFへの回転行列を、IERSの規約`m`に従って、J2000からのUT1日数で表された時刻`ut1_d`において計算します。

### 参考文献

  * IERS技術ノート No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### 参照

[`iers_era`](@ref)も参照してください。
