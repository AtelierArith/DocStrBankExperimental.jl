```
BernoulliLikelihood(l=logistic)
```

ベルヌーイ尤度は、データに関連する不確実性がベルヌーイ分布に従うと仮定する場合に使用されます。リンク `l` は、入力 `f` をドメイン [0, 1] に変換する必要があります。

$$
    p(y|f) = \operatorname{Bernoulli}(y | l(f))
$$

呼び出すと、これは `l(f)` の確率で `true` のベルヌーイ分布を返します。
