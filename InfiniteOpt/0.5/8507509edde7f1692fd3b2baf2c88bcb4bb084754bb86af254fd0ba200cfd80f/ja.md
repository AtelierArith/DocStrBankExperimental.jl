```
JuMP.is_integer(vref::UserDecisionVariableRef)::Bool
```

`JuMP.is_integer`を拡張して、`InfiniteOpt`変数が整数であるかどうかを示す`Bool`を返すようにします。

**例**

```julia-repl
julia> is_integer(vref)
true
```
