```
JuMP.objective_function(model::InfiniteModel)::JuMP.AbstractJuMPScalar
```

`JuMP.objective_function`を拡張して、無限モデル`model`の目的関数を返します。

**例**

```julia-repl
julia> objective_function(model)
1
```
