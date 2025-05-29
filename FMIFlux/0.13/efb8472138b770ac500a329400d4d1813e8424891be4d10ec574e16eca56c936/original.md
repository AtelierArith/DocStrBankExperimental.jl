DEPRECATED:

```
fmi2InputDoStepCSOutput(comp::FMU2Component, 
                        dt::Real, 
                        u::Array{<:Real})
```

Sets all FMU inputs to `u`, performs a ´´´fmi2DoStep´´´ and returns all FMU outputs.
