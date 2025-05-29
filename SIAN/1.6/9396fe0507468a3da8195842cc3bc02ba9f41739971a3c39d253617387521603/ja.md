```
macro ODEmodel(ex::Expr...)
```

方程式のリストからODEを作成し、すべての変数をグローバルスコープに注入するためのマクロ。

例:

```
ode = @ODEmodel(
    x1'(t) = - a * x1(t),
    y1(t) = x1(t),
)
```
