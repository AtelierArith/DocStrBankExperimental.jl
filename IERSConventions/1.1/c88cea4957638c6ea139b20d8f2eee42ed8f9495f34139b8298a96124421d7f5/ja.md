```
iers_pb(m::IERSModel, tt_c::Number)
```

GCRF軸から日付平均（MOD）軸へのベクトルを変換する歳差バイアス（PB）行列を計算します。これは、IERS規約 `m` に従い、`J2000` からの `TT` ジュリアン世紀で表された時刻 `tt_c` において行われます。

### 参考文献

  * Wallace P. T. と Capitaine N. (2006), IAU 2006 決議に一致する歳差- nutation 手続き, [DOI: 10.1051/0004-6361:20065897](https://www.aanda.org/articles/aa/abs/2006/45/aa5897-06/aa5897-06.html)
  * IERS 技術ノート No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS 技術ノート No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS 技術ノート No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### さらに見る

[`iers_bias`](@ref), [`iers_precession`](@ref) および [`iers_npb`](@ref) も参照してください。
