```
set_name(v::GenericVariableRef, s::AbstractString)
```

Set a variable's name attribute.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> set_name(x, "x_foo")

julia> x
x_foo

julia> name(x)
"x_foo"
```
