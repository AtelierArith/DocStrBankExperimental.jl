```
JuMP.upper_bound(vref::UserDecisionVariableRef)::Float64
```

`JuMP.upper_bound`を拡張して、`InfiniteOpt`変数の上限を返すようにします。`vref`に上限がない場合はエラーを返します。

**例**

```julia-repl
julia> upper_bound(vref)
0.0
```
