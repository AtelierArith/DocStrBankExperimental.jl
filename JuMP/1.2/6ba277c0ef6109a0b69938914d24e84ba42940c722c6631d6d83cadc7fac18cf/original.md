```
all_variables(model::Model)::Vector{VariableRef}
```

Returns a list of all variables currently in the model. The variables are ordered by creation time.

# Example

```jldoctest; setup=:(using JuMP)
model = Model()
@variable(model, x)
@variable(model, y)
all_variables(model)

# output

2-element Array{VariableRef,1}:
 x
 y
```
