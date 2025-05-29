```julia
optimized_values(
    model::ConstraintTrees.ConstraintTree,
    parameters::Dict{Symbol, Float64};
    optimizer,
    settings,
    objective,
    sense
)

```

Solve a `model` using `optimizer` by substituting in `parameters`. Optional arguments are the same as in COBREXA.

If the model does not solve successfully return `nothing`. Otherwise, return a named tuple of the solution tree, and vectors containing the values of the primal variables, the dual variables.

These duals are ordered according to the constraint output of calling [`equality_constraints`](@ref) and [`inequality_constraints`](@ref) respectively.
