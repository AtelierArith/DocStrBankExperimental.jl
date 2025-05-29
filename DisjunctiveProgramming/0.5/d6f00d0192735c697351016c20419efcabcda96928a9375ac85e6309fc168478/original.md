```
reformulate_disjunction(
    model::JuMP.AbstractModel, 
    disj::Disjunction,
    method::AbstractReformulationMethod
) where {T<:Disjunction}
```

Reformulate a disjunction using the specified `method`. Current reformulation methods include `BigM`, `Hull`, and `Indicator`. This method can be extended for other reformulation techniques.

The `disj` field is the `ConstraintData` object for the disjunction, stored in the  `disjunctions` field of the `GDPData` object.
