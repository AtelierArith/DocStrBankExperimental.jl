```
JuMP.fix_value(vref::SemiInfiniteVariableRef)::Float64
```

`JuMP.fix_value`を拡張して、`vref`の元の無限変数の固定値を返すようにします。変数が固定されていない場合はエラーになります。

**例**

```julia-repl
julia> fix_value(vref)
0.0
```
