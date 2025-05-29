```
JuMP.name(vref::DecisionVariableRef)::String
```

`JuMP.name`を拡張して`InfiniteOpt`変数の名前を返すようにします。

**例**

```julia-repl
julia> name(vref)
"var_name"
```
