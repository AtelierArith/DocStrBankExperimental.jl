```
iers_obliquity(m::IERSModel, tt_c::Number)
```

エポックにおける黄道の平均傾斜を計算します。これは、`J2000`からの`TT`ユリウス世紀で表された時刻`tt_c`におけるラジアン単位の値です。IERSの規約`m`に従います。

!!! note
    IERS 2003の規約における平均傾斜は、IAU 2000の赤道の傾斜に対する歳差率のためにIAU 1976歳差モデルへの調整をすでに考慮しています。


### 参考文献

  * IERS技術ノート No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS技術ノート No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS技術ノート No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

```
