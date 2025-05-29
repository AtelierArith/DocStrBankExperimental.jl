```
goldensection(f, (a, b); [tol=eps()])
```

関数 `f(x)` の引数最小値を `a < x < b` の範囲で見つけます。

## 例

```julia-repl
julia> goldensection(x-> (x-2)^2, (-4, 4))
2.0
```
