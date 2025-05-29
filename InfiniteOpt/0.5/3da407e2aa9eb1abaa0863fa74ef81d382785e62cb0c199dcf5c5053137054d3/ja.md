```
JuMP.has_upper_bound(vref::UserDecisionVariableRef)::Bool
```

`JuMP.has_upper_bound`を拡張して、`InfiniteOpt`変数が上限を持っているかどうかを示す`Bool`を返します。

**例**

```julia-repl
julia> has_upper_bound(vref)
true
```
