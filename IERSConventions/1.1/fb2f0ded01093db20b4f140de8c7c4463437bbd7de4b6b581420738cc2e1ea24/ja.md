```
iers_polar_motion(m::IERSModel, xₚ::Number, yₚ::Number, tt_c::Number)
```

極運動のTIRFからITRFへの回転行列を、IERSの規約に従って `m` で計算します。時間 `tt_c` は `J2000` からのTTジュリア世紀で表現されます。この関数は、国際天文基準系（ITFR）に対する天体中間極（CIP）座標である `xp` と `yp` を必要とします。

# TODO: 説明を拡張する！ (およびCPNdの仮定を確認する)

### 参考文献

  * IERS技術ノート No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS技術ノート No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS技術ノート No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

```
