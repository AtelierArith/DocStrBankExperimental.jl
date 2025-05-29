```
KernelSmoothing(X::SmoothedFreqTab; kernel = :Gaussian, hX = 0.622, scale = X.table.scale)
```

カーネルスムージングされた頻度テーブルを `KernelFreqTab` として返します。

# 引数

  * `X` クラスが `freqtab` のオブジェクト

## オプション引数

  * `kernel`
  * `hX` バンド幅。
  * `newint` 連続化された確率線を描写するための新しい区間。

# 値

`KernelFreqTab`

カーネルスムージングにおいて、バンド幅 `hX` の選択は重要な考慮事項です。バンド幅が大きいと、スムーズな分布は線形関数に等しくなります。逆に、バンド幅が小さいと、尖った形状の分布になります。デフォルト値 `hX = 6.22` を使用するか、`EstBandwidth` を使用して選択することをお勧めします。
