```
JuMP.is_fixed(vref::SemiInfiniteVariableRef)::Bool
```

`JuMP.is_fixed`を拡張して、`vref`の元の無限変数が固定されているかどうかを示す`Bool`を返します。

**例**

```julia-repl
julia> is_fixed(vref)
true
```
