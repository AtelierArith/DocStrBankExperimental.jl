```
JuMP.list_of_constraint_types(model::InfiniteModel)::Vector{Tuple{DataType, DataType}}
```

`JuMP.list_of_constraint_types`を拡張して、モデル内で使用されている関数型と集合型のすべての組み合わせを含むタプルのリストを返すようにします。

**例**

```julia-repl
julia> all_constraints(model)
3-element Array{Tuple{DataType,DataType},1}:
 (GeneralVariableRef, MathOptInterface.LessThan{Float64})
 (GeneralVariableRef, MathOptInterface.GreaterThan{Float64})
 (GeneralVariableRef, MathOptInterface.Integer)
```
