```
Disjunction{M <: JuMP.AbstractModel} <: AbstractConstraint
```

A type for a disjunctive constraint that is comprised of a collection of  disjuncts of indicated by a unique [`LogicalVariableIndex`](@ref).

**Fields**

  * `indicators::Vector{LogicalVariableref}`: The references to the logical variables

(indicators) that uniquely identify each disjunct in the disjunction.

  * `nested::Bool`: Is this disjunction nested within another disjunction?
