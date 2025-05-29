```
JuMP.objective_function_type(model::InfiniteModel)::Type{<:JuMP.AbstractJuMPScalar}
```

`JuMP.objective_function_type`を拡張して、無限モデル`model`の目的関数の型を返します。

**例**

```julia-repl
julia> objective_function_type(model)
GenericAffExpr{Float64,GeneralVariableRef}
```
