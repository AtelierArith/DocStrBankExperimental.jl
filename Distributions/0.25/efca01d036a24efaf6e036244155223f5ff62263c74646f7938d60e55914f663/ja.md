```
NormalInverseGaussian(μ,α,β,δ)
```

*ノーマル逆ガウス分布*は、位置 `μ`、尾の重さ `α`、非対称パラメータ `β`、スケール `δ` を持ち、確率密度関数は次のようになります。

$$
f(x; \mu, \alpha, \beta, \delta) = \frac{\alpha\delta K_1 \left(\alpha\sqrt{\delta^2 + (x - \mu)^2}\right)}{\pi \sqrt{\delta^2 + (x - \mu)^2}} \; e^{\delta \gamma + \beta (x - \mu)}
$$

ここで、$K_j$ は第三種の修正ベッセル関数を示します。

外部リンク

  * [ノーマル逆ガウス分布 - Wikipedia](http://en.wikipedia.org/wiki/Normal-inverse_Gaussian_distribution)
