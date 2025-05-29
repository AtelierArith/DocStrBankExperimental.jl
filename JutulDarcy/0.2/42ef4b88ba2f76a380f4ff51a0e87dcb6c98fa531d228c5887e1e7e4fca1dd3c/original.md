```
component_mass_fluxes!(q, face, state, model, flux_type, kgrad, upw)
```

Implementation of component fluxes for a given system for a given face. Should return a `StaticVector` with one entry per component.
