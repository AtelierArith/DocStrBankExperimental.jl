```
JuMP.is_integer(vref::SemiInfiniteVariableRef)::Bool
```

`JuMP.is_integer`を拡張して、`vref`の元の無限変数が整数であるかどうかを示す`Bool`を返します。

**例**

```julia-repl
julia> is_integer(vref)
true
```
