```
BayesDenoising(prior = :invgamma)
```

ベイズ推論を用いた正則化に基づくノイズ除去で、正則化パラメータを推定します。

**フィールド**

  * `prior::Symbol`: 正則化パラメータを計算するために使用されるハイパーパラメータに対する事前分布

      * `:invgamma`: 逆ガンマ分布
      * `:uniform`: 一様分布
