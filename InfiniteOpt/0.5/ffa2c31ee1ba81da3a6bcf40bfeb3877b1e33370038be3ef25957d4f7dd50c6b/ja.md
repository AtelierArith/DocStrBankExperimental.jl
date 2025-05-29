```
JuMP.lower_bound(vref::UserDecisionVariableRef)::Float64
```

`JuMP.lower_bound`を拡張して、`InfiniteOpt`変数の下限を返すようにします。`vref`に下限がない場合はエラーを返します。

**例**

```julia-repl
julia> lower_bound(vref)
0.0
```
