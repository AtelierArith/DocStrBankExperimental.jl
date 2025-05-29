```
Esat_slope(Tair; Esat_formula, constants) 
Esat_from_Tair(Tair; Esat_formula, constants) 
Esat_from_Tair_deriv(Tair; Esat_formula, constants)
```

飽和水蒸気圧 (Esat) と Esat 曲線の傾き

# 引数

  * `Tair`:      空気温度 (℃)
  * `Esat_formula=Sonntag1990()`:   使用する Esat_formula。`Sonntag1990()` (デフォルト)、`Alduchov1996()`、または `Allen1998()` のいずれか。
  * `constants=BigleafConstants()`: エントリを持つ辞書 :Pa2kPa

# 詳細

Esat (kPa) はマグヌスの方程式を使用して計算されます：

`Esat = a * exp((b * Tair) / (c + Tair)) / 1000` ここで、係数 a, b, c は使用する Esat_formula に応じて異なる値を取ります。デフォルトの値は Sonntag 1990 からのもので (a=611.2, b=17.62, c=243.12) です。このマグヌスの方程式のバージョンは WMO によって推奨されています (WMO 2008; p1.4-29)。代わりに、Alduchov & Eskridge 1996 または Allen et al. 1998 によって決定されたパラメータ値を使用することもできます (参考文献を参照)。Esat 曲線の傾き ($\Delta$) は関数の一階導関数として計算されます：

$$
\Delta = {dEsat \over dTair}
$$

# 値

  * `Esat_from_Tair`: 飽和水蒸気圧 (kPa)
  * `Esat_from_Tair_deriv`: 飽和水蒸気圧曲線の傾き (kPa K-1)
  * `Esat_slope`: 上記の2つの値のタプル

# 参考文献

Sonntag D. 1990: 1986年の物理定数の重要な新しい値、ITS-90および心理測定式に基づく水蒸気圧の定式化。 Zeitschrift fuer Meteorologie 70, 340-344.

World Meteorological Organization 2008: 気象機器および観測方法に関するガイド (WMO-No.8)。 世界気象機関、ジュネーブ。第7版、

Alduchov, O. A. & Eskridge, R. E., 1996: 飽和水蒸気圧の改善されたマグヌス形式近似。 Journal of Applied Meteorology, 35, 601-609

Allen, R.G., Pereira, L.S., Raes, D., Smith, M., 1998: 作物の蒸発散 - 作物の水要求量を計算するためのガイドライン - FAO 灌漑および排水論文 56, FAO, ローマ。

```@example
Esat_from_Tair(20.0)          # Esat in kPa
Esat_from_Tair_deriv(20.0)    # its derivative to temperature in kPa K-1
Esat_slope(20.0)              # both as a tuple
```
