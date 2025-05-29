```
pressure(model::EoSModel, V, T, z=SA[1.])
```

default units: `[Pa]`

Returns the pressure of the model at a given volume, temperature and composition, defined as:

```julia
p = -∂A/∂V
```
