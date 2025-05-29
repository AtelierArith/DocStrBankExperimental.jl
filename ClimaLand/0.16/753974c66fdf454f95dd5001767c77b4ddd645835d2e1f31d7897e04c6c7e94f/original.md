```
net_radiation!(dest,
              radiation::CoupledRadiativeFluxes,
              model::AbstractModel,
              Y,
              p,
              t)
```

Computes the net radiative flux at the ground for a coupled simulation. Your model cache must contain the field `R_n`.
