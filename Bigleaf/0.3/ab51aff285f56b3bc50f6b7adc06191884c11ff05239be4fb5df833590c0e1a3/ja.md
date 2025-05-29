```
wetbulb_temp(Tair, pressure, VPD; ...)
```

湿球温度を計算します。すなわち、空気が飽和している場合の温度です。

# 引数

  * Tair:      空気温度 (℃)
  * pressure:  大気圧 (kPa)
  * VPD:       水蒸気圧不足 (kPa)

オプション

  * accuracy:  結果の精度 (℃)
  * `Esat_formula`: [`Esat_from_Tair`](@ref)で使用される式
  * `constants=`[`BigleafConstants`](@ref)`()`: cp, eps, Pa2kPaのエントリを持つ辞書

# 詳細

湿球温度 (Tw) は次の式から計算されます：

$$
e = Esat(Tw) - gamma* (Tair - Tw)
$$

実際の水蒸気圧 e (kPa) は、[`VPD_to_e`](@ref)を使用してVPDから計算されます。心理的定数 gamma (kPa K-1) は、[`psychrometric_constant`](@ref)を使用して計算されます。

# 値

湿球温度 (℃)

# 参考文献

Monteith J.L., Unsworth M.H., 2008: Principles of Environmental Physics. 3rd edition. Academic Press, London.

# 例

```@example doc
wetbulb_temp.([20,25.0], 100, [1,1.6])             
```
