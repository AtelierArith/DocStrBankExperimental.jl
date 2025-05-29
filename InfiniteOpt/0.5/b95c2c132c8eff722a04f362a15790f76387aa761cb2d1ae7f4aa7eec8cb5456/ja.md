```
used_by_point_variable(vref::Union{InfiniteVariableRef, DerivativeRef})::Bool
```

`vref` がポイント変数によって使用されているかどうかを示す `Bool` を返します。

**例**

```julia-repl
julia> used_by_point_variable(vref)
false
```
