```
gaussian(s::AnisotropicStrategy)
```

異方性戦略 `s` のインプレース変異を実行し、次のようにガウスノイズでその変異した戦略パラメータ $\sigma$ を修正します：

  * $$
    \sigma_i^\prime = \sigma_i \exp(\tau_0 \mathcal{N}(0,1) + \tau_i \mathcal{N}(0,1))
    $$
