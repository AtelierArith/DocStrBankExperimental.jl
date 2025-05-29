```
JuMP.index(vref::GeneralVariableRef)::AbstractInfOptIndex
```

`JuMP.index`を拡張して、`vref`の適切なインデックスを返すようにします。

**例**

```julia-repl
julia> index(vref)
FiniteVariableIndex(1)
```
