```
iers_npb(m::IERSModel, tt_c::Number, δΔψ=0, δΔϵ=0)
```

ヌテーション-バイアス-前進 (NPB) 行列を計算します。この行列は、時間 `tt_c` において GCRF から日付の真軸 (TOD) へのベクトルの変換を行います。`tt_c` は `J2000` からの `TT` ジュリア世紀で表現され、IERS 規約 `m` に従います。

### 参考文献

  * Wallace P. T. と Capitaine N. (2006), IAU 2006 決議に一致する前進-ヌテーション手続き, [DOI: 10.1051/0004-6361:20065897](https://www.aanda.org/articles/aa/abs/2006/45/aa5897-06/aa5897-06.html)
  * IERS 技術ノート No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS 技術ノート No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS 技術ノート No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)

### 参照

[`iers_nutation`](@ref), [`iers_precession`](@ref) および [`iers_pb`](@ref) も参照してください。
