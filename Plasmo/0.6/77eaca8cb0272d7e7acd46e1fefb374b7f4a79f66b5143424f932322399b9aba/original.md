```
local_constraints(
    graph::OptiGraph,
    func_type::Type{<:Union{JuMP.AbstractJuMPScalar,Vector{<:JuMP.AbstractJuMPScalar}}},
    set_type::Type{<:MOI.AbstractSet},
)
```

Retrieve the local constraints with function `func_type` and set `set_type` in `graph`.  Does not include constraints in subgraphs.
