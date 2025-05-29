```
JuMP.fix_value(vref::UserDecisionVariableRef)::Float64
```

`JuMP.fix_value`を拡張して、`InfiniteOpt`変数の固定値を返すようにします。変数が固定されていない場合はエラーを返します。

**例**

```julia-repl
julia> fix_value(vref)
0.0
```
