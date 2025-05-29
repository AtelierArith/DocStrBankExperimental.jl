```
JuMP.all_constraints(
    graph::OptiGraph,
    func_type::Type{
        <:Union{JuMP.AbstractJuMPScalar,Vector{<:JuMP.AbstractJuMPScalar}},
    },
    set_type::Type{<:MOI.AbstractSet}
)
```

`graph`内のすべての制約を`func_type`と`set_type`で返します。
