```
name(con_ref::ConstraintRef)
```

Get a constraint's name attribute.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, c, [2x] in Nonnegatives())
c : [2 x] ∈ Nonnegatives()

julia> name(c)
"c"
```
