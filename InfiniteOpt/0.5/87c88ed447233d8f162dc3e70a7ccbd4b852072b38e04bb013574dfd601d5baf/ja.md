```
JuMP.has_upper_bound(vref::SemiInfiniteVariableRef)::Bool
```

`JuMP.has_upper_bound`を拡張して、`vref`の元の無限変数に上限があるかどうかを示す`Bool`を返します。

**例**

```julia-repl
julia> has_upper_bound(vref)
true
```
