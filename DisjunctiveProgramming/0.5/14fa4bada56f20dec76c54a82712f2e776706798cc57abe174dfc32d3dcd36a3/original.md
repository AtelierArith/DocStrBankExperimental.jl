```
reformulate_disjunct_constraint(
    model::JuMP.AbstractModel,  
    con::JuMP.AbstractConstraint, 
    bvref::JuMP.AbstractVariableRef,
    method::AbstractReformulationMethod
)
```

Extension point for reformulation method `method` to reformulate disjunction constraint `con` over each  constraint. If `method` needs to specify how to reformulate the entire disjunction, see  [`reformulate_disjunction`](@ref).
