散乱体のバック散乱断面積 (sigma_bs) を (S)DWBA を使用して計算します。これは、形状関数の絶対値の二乗です。

#### パラメータ

  * `s` : 散乱体オブジェクト。
  * `k` : 音響波数ベクトル。 その大きさは 2 * pi * f / c です (ここで

f は周波数、c は音速) で、伝播の方向を指します。 下向きに伝播する音波の場合、これは [0, 0, -2pi * f / c] です。

  * `phase_sd` : 各セグメントの位相変動の標準偏差 (ラジアン単位)。

デフォルトは 0.0 で、すなわち通常の決定論的 DWBA です。 0 より大きい場合、返り値は確率的になります (すなわち、SDWBA)。
