```
JuMP.lower_bound(vref::SemiInfiniteVariableRef)::Float64
```

`JuMP.lower_bound`を拡張して、`vref`の元の無限変数の下限を返します。`vref`に下限がない場合はエラーになります。

**例**

```julia-repl
julia> lower_bound(vref)
0.0
```
