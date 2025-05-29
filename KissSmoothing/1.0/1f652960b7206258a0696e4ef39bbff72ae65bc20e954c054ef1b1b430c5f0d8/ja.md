```
fit_sine_series(X::Vector,Y::Vector, basis_elements::Integer; lambda = 0.0, order=3)
```

Y ~ 1 + X + Σ sin(.) を最小化することによって Σ (Y - f(x))^2 + lambda * ∫(Δ^order F)^2 を最小化します。

```
`X` : 配列 N, N はトレーニングポイントの数です。

`Y` : 配列 N, N はトレーニングポイントの数です。

`basis_elements` : サイン項の数です。

キーワード引数:

`lambda` : 正則化の強度です。

`order` : 正則化する導関数です。
```

呼び出し可能な関数を返します。
