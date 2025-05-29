```
JuMP.num_constraints(
element::OptiElement,
function_type::Type{
    <:Union{JuMP.AbstractJuMPScalar,Vector{<:JuMP.AbstractJuMPScalar}},
},set_type::Type{<:MOI.AbstractSet})::Int64
```

要素に対する制約の総数を返します。
