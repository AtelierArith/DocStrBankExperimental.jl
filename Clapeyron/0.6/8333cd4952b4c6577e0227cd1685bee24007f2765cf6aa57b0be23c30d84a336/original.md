```
Tproperty(model::EoSModel,p,prop,z::AbstractVector,property = enthalpy;rootsolver = Roots.Order0(),phase =:unknown,abstol = 1e-15,reltol = 1e-15, verbose = false)
```

Given `p` and any other bulk property `prop` calculated via `property`, returns the required temperature `T` such that `property(model,p,T,z,phase) = prop`

Not all cases of pressure will work as `Clapeyron.bubble_temperature(model,p,z)` and `Clapeyron.dew_temperature(model,p,z)` does not always find a correct starting point.
