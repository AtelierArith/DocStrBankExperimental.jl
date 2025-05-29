```
iers_nutation_comp(m::IERSModel, tt_c::Number)
```

IERS規約`m`における経度と傾斜の摂動成分を、`J2000`からの`TT`ユリウス世紀で表された時刻`tt_c`において、ラジアンで計算します。

!!! note
    **IAU 2006A**モデルの場合、この関数はSOFAの実装に厳密に従います。最初にIAU 2000Aの摂動を計算し、その後IAU 1980の黄道からIAU 2006の黄道への傾斜の変化の結果に対する調整を適用し、(ii) 地球の動的形状因子J2の長期変化に対する調整を適用します。これらの修正により、IAU 2000Aの摂動がIAU 2006の歳差モデルと一貫性を持つことが保証されます。IERSテーブルで利用可能な係数にはすでにこれらの修正が含まれており、SOFAの経度摂動係数の振幅に1.00000047を掛けることで取得されます。


!!! note
    [`CPNc`](@ref)および[`CPNd`](@ref)モデルのこれらの成分の表現は、間接的にそのCIP級数展開から計算されます。


!!! warning
    自由コア摂動および時間依存効果の計算はこのモデルから除外されています。IAU 2006/2000 A歳差-摂動モデルで< 1μasの精度を達成するためには、そのような効果を事後的に（δΔψおよびδΔϵを通じて）IERS EOPデータを使用して含める必要があります。


### References

  * IERS Technical Note No. [21](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn21.html)
  * IERS Technical Note No. [32](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn32.html)
  * IERS Technical Note No. [36](https://www.iers.org/IERS/EN/Publications/TechnicalNotes/tn36.html)
  * Wallace P. T. and Capitaine N. (2006), IAU 2006の決議に一致する歳差-摂動手続き, [DOI: 10.1051/0004-6361:20065897](https://www.aanda.org/articles/aa/abs/2006/45/aa5897-06/aa5897-06.html)
  * Capitaine N. and Wallace P. T. (2008), 簡潔なCIOに基づく歳差-摂動の定式化
  * ERFA [nut06a](https://github.com/liberfa/erfa/blob/master/src/nut06a.c)および[nut00b](https://github.com/liberfa/erfa/blob/master/src/nut00b.c)関数

### See also

See also [`iers_nutation`](@ref)
