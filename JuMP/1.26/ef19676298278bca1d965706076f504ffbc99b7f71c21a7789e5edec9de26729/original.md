```
constraint_by_name(model::AbstractModel, name::String, [F, S])::Union{ConstraintRef,Nothing}
```

Return the reference of the constraint with name attribute `name` or `Nothing` if no constraint has this name attribute.

Throws an error if several constraints have `name` as their name attribute.

If `F` and `S` are provided, this method addititionally throws an error if the constraint is not an `F`-in-`S` contraint where `F` is either the JuMP or MOI type of the function and `S` is the MOI type of the set.

Providing `F` and `S` is recommended if you know the type of the function and set since its returned type can be inferred while for the method above (that is, without `F` and `S`), the exact return type of the constraint index cannot be inferred.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @constraint(model, con, x^2 == 1)
con : x² = 1

julia> constraint_by_name(model, "kon")

julia> constraint_by_name(model, "con")
con : x² = 1

julia> constraint_by_name(model, "con", AffExpr, MOI.EqualTo{Float64})

julia> constraint_by_name(model, "con", QuadExpr, MOI.EqualTo{Float64})
con : x² = 1
```
