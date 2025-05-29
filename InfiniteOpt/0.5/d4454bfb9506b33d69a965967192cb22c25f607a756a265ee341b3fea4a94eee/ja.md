```
JuMP.reduced_cost(vref::GeneralVariableRef)
```

`JuMP.reduced_cost`を拡張します。これは変数の削減コストを返します。これは無限変数の場合はスカラー値のベクトルになり、有限変数の場合はスカラー値になります。

**例**

```julia-repl
julia> reduced_cost(x)
12.81
```
