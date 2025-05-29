```
index(v::GenericVariableRef)::MOI.VariableIndex
```

Return the index of the variable that corresponds to `v` in the MOI backend.

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> index(x)
MOI.VariableIndex(1)
```
