```
mapleaves(f, [style = WalkStyle], x)
```

`f`を`x`の各リーフノードに適用し、結果を返します。`f`はリーフノードのみを見ることができます。

# 例

```julia-repl
julia> mapleaves(x -> @show(x) isa Integer ? x + 1 : x, (a=2, b=(c=4, d=0)))
x = 2
x = 4
x = 0
(a = 3, b = (c = 5, d = 1))

```
