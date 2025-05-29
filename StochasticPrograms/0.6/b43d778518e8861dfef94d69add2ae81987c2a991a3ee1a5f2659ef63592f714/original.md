```
@parameters(def)
```

Define the problem parameters in a @stage block

```julia
@parameters param1, param2, ...
```

possibly with default values. Any defined parameter without a default value must be supplied as a keyword argument to [`instantiate`](@ref) when creating models.

## Examples

```julia
@parameters d

@parameters begin
    Crops = [:wheat, :corn, :beets]
    Cost = Dict(:wheat=>150, :corn=>230, :beets=>260)
    Budget = 500
end
```

See also [`@decision`](@ref), [`@uncertain`](@ref), [`@stage`](@ref)
