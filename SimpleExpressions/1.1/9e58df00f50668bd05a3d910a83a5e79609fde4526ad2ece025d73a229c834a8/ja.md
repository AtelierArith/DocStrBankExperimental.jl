```
solve(eq::SymboliclEquation, x)
```

非常に*単純な*記号方程式は、エクスポートされていない`solve`メソッドで解くことができます。この例は使用法を示しています。

```{julia}
@symbolic w p; @symbolic h  # 2つの変数、1つのパラメータ
import SimpleExpressions: solve, D
constraint = p ~ 2w + 2h
A = w * h

u = solve(constraint, h)
A = A(u) # 置換に方程式を使用
v = solve(D(A, w) ~ 0, w)
```
