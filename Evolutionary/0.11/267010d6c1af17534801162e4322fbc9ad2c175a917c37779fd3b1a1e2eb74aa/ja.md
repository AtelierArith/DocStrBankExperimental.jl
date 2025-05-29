```
gaussian(x, s::AnisotropicStrategy)
```

再組合された `x` に対して、戦略 `s` に基づいてガウス異方性変異を実行します。ガウスノイズを次のように加えます：

  * $$
    x_i^\prime = x_i + s.\sigma_i \mathcal{N}_i(0,1)
    $$
