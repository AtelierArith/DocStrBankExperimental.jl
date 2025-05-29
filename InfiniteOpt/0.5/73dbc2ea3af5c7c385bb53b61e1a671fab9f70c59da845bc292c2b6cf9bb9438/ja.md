```
JuMP.has_lower_bound(vref::SemiInfiniteVariableRef)::Bool
```

`JuMP.has_lower_bound`を拡張して、`vref`の元の無限変数に下限があるかどうかを示す`Bool`を返します。

**例**

```julia-repl
julia> has_lower_bound(vref)
true
```
