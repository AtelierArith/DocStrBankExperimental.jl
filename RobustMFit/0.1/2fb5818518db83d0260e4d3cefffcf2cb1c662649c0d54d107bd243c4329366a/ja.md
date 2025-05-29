```
dPower(d::UnivariateDistribution, p::Int64)
```

単変量確率変数 X の累乗を記述するデータ型。X の分布 `d` と整数 `i` が与えられたとき、この型は $X^i$ を記述します。

# 例

```julia
    dX = Poisson(10)
    dY = dPower(d, 2)
```
