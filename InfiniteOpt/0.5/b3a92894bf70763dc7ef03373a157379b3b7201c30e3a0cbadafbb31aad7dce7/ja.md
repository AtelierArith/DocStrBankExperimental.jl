```
JuMP.is_valid(model::InfiniteModel, cref::InfOptConstraintRef)::Bool
```

`JuMP.is_valid`を拡張して、`InfiniteOpt`制約参照が有効かどうかを示す`Bool`を返します。

**例**

```julia-repl
julia> is_valid(model, cref)
true
```
