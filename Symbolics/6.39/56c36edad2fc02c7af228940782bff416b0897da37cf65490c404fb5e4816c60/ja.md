```
terms(x)
```

シンボリック表現 `x` の項を取得します。

# 例

```julia-repl
julia> terms(-x + y - z)
3-element Vector{Num}:
 -z
  y
 -x
```
