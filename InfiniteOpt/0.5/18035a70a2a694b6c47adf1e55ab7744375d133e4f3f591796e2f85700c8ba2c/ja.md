```
JuMP.is_valid(model::InfiniteModel, vref::GeneralVariableRef)::Bool
```

`JuMP.is_valid`を拡張して、`vref`が有効な参照である場合に`Bool`を返すようにします。

**例**

```julia-repl
julia> is_valid(model, vref)
true
```
