```
turbulent_fluxes!(dest,
                atmos::CoupledAtmosphere,
                model::AbstractModel,
                Y,
                p,
                t)
```

Computes the turbulent surface fluxes terms at the ground for a coupled simulation. In this case, the coupler has already computed turbulent fluxes and updated them in each of the component models, so this function does nothing.
