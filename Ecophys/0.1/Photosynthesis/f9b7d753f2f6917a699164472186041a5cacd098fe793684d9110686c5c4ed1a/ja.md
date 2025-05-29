```
energybalance(pgb, pAgs, pEb, PAR, NIR, ws, RH, Tair, Ca, P, O2)
```

葉のエネルギーバランスを計算します。

# 引数

  * `pgb`: 境界層伝導モデル
  * `pAgs`: 光合成および気孔伝導モデル
  * `pEb`: 葉の光学特性
  * `PAR`: 光合成に活性な放射線 (umol/m2/s)
  * `NIR`: 近赤外線放射 (W/m2)
  * `ws`: 風速 (m/s)
  * `RH`: 相対湿度
  * `Tair`: 空気温度 (K)
  * `Ca`: 大気中のCO2濃度 (μmol/mol)
  * `P`: 気圧 (kPa)
  * `O2`: 大気中のO2濃度 (μmol/mol)

# 詳細

入力は `Real` または `Quantity` 型（すなわち、物理単位を持つ）である場合があります。`Quantity` 型が使用される場合、出力は `Quantity` 型になります。
