```
LogicalVariable <: JuMP.AbstractVariable
```

A variable type the logical variables associated with disjuncts in a [`Disjunction`](@ref).

**Fields**

  * `fix_value::Union{Nothing, Bool}`: A fixed boolean value if there is one.
  * `start_value::Union{Nothing, Bool}`: An initial guess if there is one.
