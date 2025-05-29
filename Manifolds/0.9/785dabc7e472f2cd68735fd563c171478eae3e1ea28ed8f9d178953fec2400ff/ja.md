```
project(
    M::AbstractMultinomialDoublyStochastic,
    p;
    maxiter = 100,
    tolerance = eps(eltype(p))
)
```

正のエントリを持つ行列 `p` をSinkhornのアルゴリズムを適用して射影します。このprojectメソッドは、通常のケースとは異なり、キーワードを受け入れます。
