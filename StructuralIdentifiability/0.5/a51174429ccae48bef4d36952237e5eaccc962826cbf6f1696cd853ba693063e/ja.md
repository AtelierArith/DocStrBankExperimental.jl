```
macro ODEmodel
```

方程式のリストからODEを作成するためのマクロです。また、すべての変数をグローバルスコープに注入します。

## 例

単純な`ODE`を作成する：

```jldoctest
using StructuralIdentifiability

ode = @ODEmodel(
    x1'(t) = a * x1(t) + u(t),
    x2'(t) = b * x2(t) + c*x1(t)*x2(t),
    y(t) = x1(t)
)
```

ここで、

  * `x1`、`x2`は状態変数です
  * `y`は出力変数です
  * `u`は入力変数です
  * `a`、`b`、`c`は時間に依存しないパラメータです
