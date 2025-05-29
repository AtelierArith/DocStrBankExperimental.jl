```
parameter_by_name(model::InfiniteModel,
                  name::String)::Union{GeneralVariableRef, Nothing}
```

Return the parameter reference assoociated with a parameter name. Errors if multiple parameters have the same name. Returns nothing if no such name exists.

**Example**

```julia-repl
julia> parameter_by_name(model, "t")
t
```
