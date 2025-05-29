```
@hydromodel name begin
    component1
    component2
    ...
end
```

Creates a HydroModel with the specified name and components.

# Arguments

  * `name`: Symbol for the model name
  * Components can be:

      * HydroBucket instances
      * Flux definitions (using @hydroflux, @neuralflux, etc.)
      * Other model components

# Example

```julia
@hydromodel :model1 begin
    bucket1
    @neuralflux :flux1 [y] ~ chain([x1, x2])
    bucket2
end
```
