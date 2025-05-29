```
gb(p::gbType, ws, Tleaf, Tair, P)
```

熱、水蒸気、CO2の境界層伝導率を計算します。

# 引数

  * `p`: 境界層伝導率のモデル
  * `ws`: 風速 (m/s)
  * `Tleaf`: 葉の温度 (K)
  * `Tair`: 空気の温度 (K)
  * `P`: 空気圧 (Pa)

# 戻り値

  * `gbh`: 熱の境界層伝導率 (mol/m2/s)
  * `gbw`: 水蒸気の境界層伝導率 (mol/m²/s)
  * `gbc`: CO2の境界層伝導率 (mol/m²/s)
