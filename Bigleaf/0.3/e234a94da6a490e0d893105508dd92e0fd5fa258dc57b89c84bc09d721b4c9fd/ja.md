```
dew_point(Tair,VPD; ...)
dew_point_from_e(ea; ...)
```

露点を計算します。空気が飽和状態になるために冷却されなければならない温度（i*e* e = Esat(Td)）

# 引数

  * Tair:     空気温度 (℃)
  * VPD:      水蒸気圧不足 (kPa)
  * ea:       実際の水蒸気圧 (kPa)

オプション

  * accuracy = 1e-03: 結果の精度 (℃)
  * `Esat_formula`: [`Esat_from_Tair`](@ref) で使用される式
  * `constants=`[`BigleafConstants`](@ref)`()`: Pa2kPa のエントリを持つ辞書

# 詳細

露点温度 (Td) は、飽和水蒸気圧が現在の水蒸気圧に等しくなる温度として定義されます。すなわち、水が凝縮し始める温度です。

$$
e = Esat(Td)
$$

ここで、e は空気の水蒸気圧であり、Esat は水蒸気圧不足です。この方程式は最適化によって Td を解決します。

# 値

露点温度 (℃)

# 参考文献

Monteith J.L., Unsworth M.H., 2008: Principles of Environmental Physics. 3rd edition. Academic Press, London.

# 例

```@example doc
Tair = 20.0
VPD = 1.5
Td = dew_point(Tair, VPD; accuracy = 1e-2)                
(e = VPD_to_e(VPD,Tair), esat_Td = Esat_from_Tair(Td))
```
