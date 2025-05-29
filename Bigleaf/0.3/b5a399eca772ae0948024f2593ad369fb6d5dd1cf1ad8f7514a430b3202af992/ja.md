```
pressure_from_elevation(elev,Tair,VPD=missing;...)
```

与えられた標高での平均圧力の推定値を、ヒプソメトリック方程式によって予測します。

# 引数

  * elev:      標高 a*s*l_ (m)
  * Tair:      空気温度 (℃)
  * VPD:       水蒸気圧不足 (kPa); オプション

オプション 

  * `constants=`[`BigleafConstants`](@ref)`()`: エントリを持つ辞書 Kelvin, pressure0, Rd, g, Pa2kPa

# 詳細

大気圧はヒプソメトリック方程式によって近似されます：

$$
pressure = pressure_0 / (exp(g * elevation / (Rd Temp)))
$$

ヒプソメトリック方程式は、特定の高度での標準圧力の推定値を提供します。 VPDが提供されると、湿度補正が適用され、空気温度の代わりに仮想温度が使用されます。 VPDは内部的に比湿に変換されます。

# 値

大気圧 (kPa)

# 参考文献

Stull B_, 1988: An Introduction to Boundary Layer Meteorology.             Kluwer Academic Publishers, Dordrecht, Netherlands.

# 例

```@example doc
# 25℃および1 kPaのVPDでの500mの高度での平均圧力
pressure_from_elevation(500,25,1)
```
