```
(value, sigma) = snr(G1::GraphSig, G2::GraphSig, stdp::Bool = false)

G1（元の信号）とG2（ノイズ信号）間のSNRを計算します
```

### 入力引数

  * `G1::GraphSig`: 元の参照グラフ信号
  * `G2::GraphSig`: 復元されたまたはノイズのあるグラフ信号
  * `stdp::Bool`: 差の標準偏差を計算するかどうかを指定するフラグ

### 出力引数

  * `value`: dB単位の信号/ノイズ比
  * `sigma`: ノイズの標準偏差（stdp == trueの場合）
