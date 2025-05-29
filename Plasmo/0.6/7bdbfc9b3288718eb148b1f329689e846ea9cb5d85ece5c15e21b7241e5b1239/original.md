```
JuMP.all_constraints(
    graph::OptiGraph,
    func_type::Type{
        <:Union{JuMP.AbstractJuMPScalar,Vector{<:JuMP.AbstractJuMPScalar}},
    },
    set_type::Type{<:MOI.AbstractSet}
)
```

Return all of the constraints in `graph` with `func_type` and `set_type`.
