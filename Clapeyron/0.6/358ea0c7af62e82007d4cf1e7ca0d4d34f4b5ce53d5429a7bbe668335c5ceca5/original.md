```
partial_property(model::EoSModel, p, T, z, property::X; phase=:unknown, threaded=true, vol0=nothing) where {X}
```

Calculate the partial molar property of a mixture at specified temperature, pressure, mol amounts, and extensive property of interest. The equality `sum(z .* partial_property(model,p,T,z,property) - property(model,p,T,z))` should hold.

The keywords `phase`, `threaded` and `vol0` are passed to the [`Clapeyron.volume`](@ref) solver.
