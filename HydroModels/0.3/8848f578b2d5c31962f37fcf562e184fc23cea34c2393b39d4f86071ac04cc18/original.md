```
@neuralbucket name begin
    fluxes = begin
        ...
    end
    dfluxes = begin
        ...
    end
end
```

Creates a HydroBucket with the specified name, fluxes, and dfluxes.

# Arguments

  * `name`: Symbol for the bucket name
  * `fluxes`: Array of HydroFlux or NeuralFlux objects
  * `dfluxes`: Array of StateFlux objects

# Example

```julia
@hydrobucket :bucket1 begin
    fluxes = [flux1, flux2]
    dfluxes = [dflux1, dflux2]
end
```
