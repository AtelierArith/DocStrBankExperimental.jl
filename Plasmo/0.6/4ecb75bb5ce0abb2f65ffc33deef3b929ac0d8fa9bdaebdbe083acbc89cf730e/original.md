```
num_local_link_constraints(
    graph::OptiGraph,
    func_type::Type{<:Union{JuMP.AbstractJuMPScalar,Vector{<:JuMP.AbstractJuMPScalar}}},
    set_type::Type{<:MOI.AbstractSet},
)
```

Retrieve the number of local linking constraints with function `func_type` and set  `set_type` in `graph`. Does not include linking constraints in subgraphs.
