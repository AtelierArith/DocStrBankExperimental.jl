```
gaussian(x, s::IsotropicStrategy)
```

再組合された `x` に対して、戦略 `s` に基づいてガウス等方性変異を実行します。ガウスノイズを次のように加えます：

  * $$
    x_i^\prime = x_i + s.\sigma \mathcal{N}_i(0,1)
    $$
