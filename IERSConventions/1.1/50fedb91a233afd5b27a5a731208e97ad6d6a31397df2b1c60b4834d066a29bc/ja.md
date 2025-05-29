```
iers_nutation(m::IERSModel, tt_c::Number, δΔψ::Number=0, δΔϵ::Number=0)
```

平均日付 (MOD) 軸から日付の真軸 (TOD) 軸へのベクトルを回転させるヌテーション行列を、IERS 規約 `m` に従って、`J2000` からの `TT` ジュリアン世紀で表現された時刻 `tt_c` において計算します。

オプションの EOP ヌテーション補正は、`δΔψ` および `δΔϵ` パラメータを介して提供できます。

### 参考文献

  * Wallace P. T. と Capitaine N. (2006), IAU 2006 決議に一致する歳差-ヌテーション手続き, [DOI: 10.1051/0004-6361:20065897](https://www.aanda.org/articles/aa/abs/2006/45/aa5897-06/aa5897-06.html)

### 参照

[`iers_nutation_comp`](@ref) および [`iers_obliquity`](@ref) も参照してください。 
