```
is_used(vref::Union{InfiniteVariableRef, DerivativeRef})::Bool
```

モデル内で `vref` が使用されているかどうかを示す `Bool` を返します。

**例**

```julia-repl
julia> is_used(vref)
false
```
