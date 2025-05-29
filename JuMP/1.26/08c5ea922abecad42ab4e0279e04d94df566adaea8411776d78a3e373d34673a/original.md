```
name(v::GenericVariableRef)::String
```

Get a variable's name attribute.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2])
2-element Vector{VariableRef}:
 x[1]
 x[2]

julia> name(x[1])
"x[1]"
```
