```
bisection(f, (a, b); [tol=eps()])
```

方程式 `f(x) = 0` の根を `a < x < b` の範囲で見つけます。

この方法は `f(a) * f(b) < 0` の場合にのみ機能します。

## 例

```julia-repl
julia> bisection(sin, (2, 4))
3.141592653589793
```
