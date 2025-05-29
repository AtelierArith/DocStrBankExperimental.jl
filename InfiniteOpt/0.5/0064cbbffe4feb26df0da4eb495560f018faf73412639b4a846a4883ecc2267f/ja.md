```
JuMP.name(cref::InfOptConstraintRef)::String
```

`JuMP.name`を拡張して、`InfiniteOpt`制約の名前を返すようにします。

**例**

```julia-repl
julia> name(cref)
"constr_name"
```
