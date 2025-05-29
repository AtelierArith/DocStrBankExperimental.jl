```
texpr2expr(x, m::Module=Main)
```

は、lispのようなタプル式 `x` をJuliaの実行可能な式に変換します。

例: `sin(π/6)` の式

```julia
julia> texpr2expr((:call, :sin, (:call, :/, π, 6)))
:(sin(π / 6))
```
