```
JuMP.is_binary(vref::SemiInfiniteVariableRef)::Bool
```

`JuMP.is_binary`を拡張して、`vref`の元の無限変数がバイナリであるかどうかを示す`Bool`を返します。

**例**

```julia-repl
julia> is_binary(vref)
true
```
