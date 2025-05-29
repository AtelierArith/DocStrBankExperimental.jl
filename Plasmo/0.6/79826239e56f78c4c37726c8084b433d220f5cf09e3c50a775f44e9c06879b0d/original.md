```
num_link_constraints(
    graph::OptiGraph,
    func_type::Type{<:Union{JuMP.AbstractJuMPScalar,Vector{<:JuMP.AbstractJuMPScalar}}},
    set_type::Type{<:MOI.AbstractSet},
)
```

Retrieve the total number of linking constraints with function `func_type` and set  `set_type` in `graph`. Includes constraints in subgraphs.
