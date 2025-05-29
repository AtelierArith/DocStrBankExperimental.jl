```
status(m)
status(m::AbstractArray{<:ModelList})
status(m::AbstractDict{T,<:ModelList})
```

Get a ModelList status, *i.e.* the state of the input (and output) variables.

See also [`is_initialized`](@ref) and [`to_initialize`](@ref)

# Examples

```jldoctest
using PlantSimEngine

# Including example models and processes:
using PlantSimEngine.Examples;

# Create a ModelList
models = ModelList(
    process1=Process1Model(1.0),
    process2=Process2Model(),
    process3=Process3Model(),
    status = (var1=[15.0, 16.0], var2=0.3)
);

status(models)

# Or just one variable:
status(models,:var1)


# Or the status at the ith time-step:
status(models, 2)

# Or even more simply:
models[:var1]
# output
2-element Vector{Float64}:
 15.0
 16.0
```
