```
BayesianLinearRegressor{Tmw, TΛw}
```

ベイズ線形回帰器は、次のように与えられる線形関数の分布です。

```julia
w ~ Normal(mw, Λw)
f(x) = dot(x, w)
```

ここで、`mw` と `Λw` はそれぞれ `w` の平均と精度です。
