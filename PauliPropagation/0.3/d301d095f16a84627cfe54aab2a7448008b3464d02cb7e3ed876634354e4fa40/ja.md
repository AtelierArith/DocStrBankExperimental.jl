```
DephasingNoise(qind::Int)
DephasingNoise(qind::Int, p::Real)
```

これは `PauliZNoise` のエイリアスです。インデックス `qind` のキュービットに作用する脱相関ノイズチャネルです。XおよびYパウリを `1-p` の因子で等しく減衰させます。`p` が提供されると、このノイズ強度を持つフローズンゲートが返されます。
