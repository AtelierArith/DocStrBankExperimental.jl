```
JuMP.start_value(vref::UserDecisionVariableRef)::Union{Nothing, Float64}
```

`JuMP.start_value`を拡張して、`InfiniteOpt`変数の開始値を返すようにします。開始値がない場合は`nothing`を返します。

**例**

```julia-repl
julia> start_value(vref)
0.0
```
