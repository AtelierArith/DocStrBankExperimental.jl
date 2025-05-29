```
JuMP.has_lower_bound(vref::UserDecisionVariableRef)::Bool
```

`JuMP.has_lower_bound`を拡張して、`InfiniteOpt`変数が下限を持つかどうかを示す`Bool`を返します。

**例**

```julia-repl
julia> has_lower_bound(vref)
true
```
