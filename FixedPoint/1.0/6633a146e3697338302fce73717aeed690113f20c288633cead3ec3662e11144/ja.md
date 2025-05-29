```
afps(f, x; iters::Int = 5000, vel::Float64 = 0.9, ep::Float64 = 0.01, tol::Float64 = 1e-12, grad_norm=x->maximum(abs,x))
```

方程 `f(x) = x` を次のように解きます：

```
`f` : 固定点を見つけるための関数

`x` : 初期条件、理想的には最終解に近いべきです

`vel` : Nesterov加速の量 [0,1] の範囲

`ep` : 学習率、通常は ]0,1[ の範囲

`tol` : |f(x)-x| に対する絶対許容誤差

`grad_norm` : |f(x)-x| のノルムを評価するための関数
```

名前付きタプル (x, error, iters) を返します：

```
`x` : f(x)=x のために見つかった解

`error` : 解の点での f(x)-x のノルム

`iters` : 実行された総反復回数
```
