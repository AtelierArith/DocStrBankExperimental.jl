```
AmplitudeDampingNoise(qind::Int)
```

インデックス `qind` のキュービットに作用する振幅減衰ノイズチャネル。XおよびYパウリをsqrt(1-gamma)の因子で減衰させ、Zをgamma * Iおよび(1-gamma) * Z成分に分割します（転置ハイゼンベルグ画像において）。
