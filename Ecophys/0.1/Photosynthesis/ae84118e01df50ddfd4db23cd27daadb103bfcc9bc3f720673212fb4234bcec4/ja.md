```
solve_energy_balance(Ags::Union{C3Q, C4Q}; gb = simplegbQ(),
                     opt = SimpleOptical(), PAR = 1000.0μmol/m^2/s,
                     NIR = 250.0W/m^2, ws = 1.0m/s, RH = 0.75,
                     Tair = 298.0K, Ca = 400.0μmol/mol, P = 101.0kPa,
                     O2 = 210.0mmol/mol, order = Order2(), xatol = 0.01,
                     maxfnevals = 100, net = true)
solve_energy_balance(Ags::Union{C3, C4}; gb = simplegb(),
                     opt = SimpleOptical(), PAR = 1000.0, NIR = 250.0,
                     ws = 1.0, RH = 0.75, Tair = 298.0, Ca = 400.0,
                     P = 101.0e3, O2 = 210.0e3, order = Order2(), xatol = 0.01,
                     maxfnevals = 100, net = true)
```

葉のエネルギーバランスを光合成と蒸散に結びつけて解決します。

# 引数

  * `Ags`: 光合成および気孔伝導モデル
  * `gb`: 境界層伝導モデル
  * `opt`: 葉の光学特性
  * `PAR`: 光合成に活性な放射線 (umol/m2/s)
  * `NIR`: 近赤外線放射 (W/m2)
  * `ws`: 風速 (m/s)
  * `RH`: 相対湿度
  * `Tair`: 空気温度 (K)
  * `Ca`: 大気中のCO2濃度 (μmol/mol)
  * `P`: 空気圧 (Pa)
  * `O2`: 大気中のO2濃度 (μmol/mol)
  * `order`: 葉温を求めるための根解法アルゴリズムの順序 (詳細はRoots.jlパッケージを参照)。
  * `xatol`: 根解法アルゴリズムの絶対許容誤差 (詳細はRoots.jlパッケージを参照)。
  * `maxfnevals`: 根解法アルゴリズムの最大関数評価回数 (詳細はRoots.jlパッケージを参照)。
  * `net`: 正味または総CO2同化を返すかどうか。

# 詳細

入力は `Real` または Unitful.jl の `Quantity` タイプ（すなわち物理単位を持つ）である場合があります。`Quantity` タイプが使用される場合、出力は `Quantity` タイプになります。

# 戻り値

正味CO2同化量 (`An`, μmol/m^2/s)、総CO2同化量 (`Ag`, μmol/m^2/s)、蒸散量 (`Tr`, mol/m^2/s)、および葉温 (`Tleaf`, K) を含む名前付きタプル。
