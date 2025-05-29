```
used_by_semi_infinite_variable(vref::Union{InfiniteVariableRef, DerivativeRef})::Bool
```

`vref` が半無限変数によって使用されているかどうかを示す `Bool` を返します。

**例**

```julia-repl
julia> used_by_semi_infinite_variable(vref)
false
```
