```
JuMP.num_constraints(
element::OptiElement,
function_type::Type{
    <:Union{JuMP.AbstractJuMPScalar,Vector{<:JuMP.AbstractJuMPScalar}},
},set_type::Type{<:MOI.AbstractSet})::Int64
```

Return the total number of constraints on an element.
