```
shrink_eqs(::Vector{Equation})
shrink_eqs(::Vector{Equation}, ::Int)
```

与えられた一連の記号方程式に対して、LHS項のRHS定義を段階的に置き換え、残る方程式の数が指定された数になるまで進めます（デフォルト = 4）。

# 例

```
eqs = [y ~ 15*x,
       z ~ (1+y)^2]
shrink_eqs(eqs, 1)

1-element Vector{Equation}:
 z ~ (1 + 15x)^2
```
