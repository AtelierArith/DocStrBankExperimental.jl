```
loglikelihood(v::IHTVariable{T, M})
```

観測値 `y` の対数尤度を計算します。ここで、平均 `μ = E(y) = g^{-1}(xβ)` といくつかの一変量分布 `d` が与えられます。

対数尤度は各観測値の対数確率密度関数の合計であることに注意してください。
