```
info.αbest
AMORS.best_scaling_factor(info::AMORS.Info)
AMORS.best_scaling_factor(μ, J(x), q, ν, K(y), r)
AMORS.best_scaling_factor(μ*J(x), q, ν*K(y), r)
```

は次のように定義される最適スケーリングファクターを返します：

```
α⁺ = argmin_{α > 0} μ*J(α*x) + ν*K(y/α)
```

そして、閉じた形の表現を持ちます：

```
α⁺ = ((r*ν*K(y))/(q*μ*J(x)))^(1/(q + r))
```

引数は、均質関数 `J(x)` と `K(y)` の値、対応する乗数 `μ` と `ν`、および双線形モデルの変数 `x` と `y` の現在の推定値に対するそれぞれの次数 `q = deg(J)` と `r = deg(K)` です。これらの引数はすべて、AMORSアルゴリズムの状態 `info` によって提供される可能性があります。
