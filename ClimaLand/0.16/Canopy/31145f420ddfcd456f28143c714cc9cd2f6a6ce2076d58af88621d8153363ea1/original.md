```
 ClimaLand.make_compute_imp_tendency(component::AbstractCanopyComponent, canopy)
```

Creates the compute*imp*tendency!(dY,Y,p,t) function for the canopy `component`.

Since component models are not standalone models, other information may be needed and passed in (via the `canopy` model itself). The right hand side for the entire canopy model can make use of these functions for the individual components.
