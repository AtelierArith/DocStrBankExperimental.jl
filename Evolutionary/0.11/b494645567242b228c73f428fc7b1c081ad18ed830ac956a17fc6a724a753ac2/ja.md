```
gaussian(s::IsotropicStrategy)
```

アイソトロピック戦略 `s` のインプレース変異を実行し、次のようにガウスノイズでその変異した戦略パラメータ $\sigma$ を修正します：

  * $$
    \sigma^\prime = \sigma \exp(\tau_0 \mathcal{N}(0,1))
    $$
