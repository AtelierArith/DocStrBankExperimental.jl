```
JuMP.is_fixed(vref::UserDecisionVariableRef)::Bool
```

`JuMP.is_fixed`を拡張して、`InfiniteOpt`変数が固定されているかどうかを示す`Bool`を返します。

**例**

```julia-repl
julia> is_fixed(vref)
true
```
