```
speed_of_sound(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

default units: `[m/s]`

Calculates the speed of sound, defined as:

```julia
c = V * √(∂²A/∂V² - ∂²A/∂V∂T^2 / ∂²A/∂T²)/Mr)
```

Where `Mr` is the molecular weight of the model at the input composition.

Internally, it calls [`Clapeyron.volume`](@ref) to obtain `V` and calculates the property via `VT_speed_of_sound(model,V,T,z)`.

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.

!!! warning "Accurate ideal model required"
    This property requires at least second order ideal model temperature derivatives. If you are computing these properties, consider using a different ideal model than the `BasicIdeal` default (e.g. `EoS(["species"];idealmodel = ReidIdeal)`).

