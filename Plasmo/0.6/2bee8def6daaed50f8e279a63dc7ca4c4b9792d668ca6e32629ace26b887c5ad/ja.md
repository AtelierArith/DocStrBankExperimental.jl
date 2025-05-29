```
JuMP.num_constraints(
    graph::OptiGraph,
    func_type::Type{<:Union{JuMP.AbstractJuMPScalar,Vector{<:JuMP.AbstractJuMPScalar}}},
    set_type::Type{<:MOI.AbstractSet},
)
```

`graph`内の`func_type`と`set_type`を持つすべての制約の数を返します。
