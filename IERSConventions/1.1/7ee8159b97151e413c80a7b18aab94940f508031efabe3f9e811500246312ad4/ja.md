```
iers_era(m::IERSModel, ut1_d::Number)
```

地球回転角 (ERA) を計算します。これは、IERS 方式 `m` に従って、`J2000` からの UT1 日数で表された時刻 `ut1_d` におけるラジアン単位の値です。

!!! note
    IERS 1996 方式では、θ は星の角度として言及されています。


### 参考文献

  * IERS 技術ノート No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS 技術ノート No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### 参照

[`iers_era_rotm`](@ref) も参照してください。 ```
