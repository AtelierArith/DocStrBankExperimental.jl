```
HeteroscedasticGaussianLikelihood(l=exp)
```

ヘテロスケダスティックガウス尤度。これは、平均と分散が潜在プロセスの関数であるガウス尤度です。

$$
    p(y|[f, g]) = \operatorname{Normal}(y | f, sqrt(l(g)))
$$

呼び出すと、平均 `f` と分散 `l(g)` を持つ正規分布が返されます。ここで、`l` は R から R^+ へのリンクです。
