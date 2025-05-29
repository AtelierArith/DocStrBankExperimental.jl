```
@genfun(expr, args)
```

与えられた `expr` と `args` に基づいて匿名関数を返します。

```Julia
julia> @genfun x^2+y^2 x y
```
