```
JuMP.upper_bound(vref::SemiInfiniteVariableRef)::Float64
```

`JuMP.upper_bound`を拡張して、`vref`の元の無限変数の上限を返します。`vref`に上限がない場合はエラーになります。

**例**

```julia-repl
julia> upper_bound(vref)
0.0
```
