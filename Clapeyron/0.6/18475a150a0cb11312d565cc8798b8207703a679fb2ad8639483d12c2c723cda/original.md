```
mass_density(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true)
```

default units: `[kg/m^3]`

Calculates the mass density, defined as:

```julia
ρₙ = Mr/V
```

Where `Mr` is the molecular weight of the model at the input composition.

Internally, it calls [`Clapeyron.volume`](@ref) to obtain `V` and calculates the property via `VT_mass_density(model,V,T,z)`.

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.
