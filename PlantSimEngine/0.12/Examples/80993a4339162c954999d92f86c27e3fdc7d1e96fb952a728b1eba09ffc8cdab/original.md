```
fit(::Type{Beer}, df; J_to_umol=PlantMeteo.Constants().J_to_umol)
```

Compute the `k` parameter of the Beer-Lambert law from measurements.

# Arguments

  * `::Type{Beer}`: the model type
  * `df`: a `DataFrame` with the following columns:

      * `aPPFD`: the measured absorbed Photosynthetic Photon Flux Density in μmol[PAR] m[leaf]⁻² s⁻¹
      * `LAI`: the measured leaf area index in m² m⁻²
      * `Ri_PAR_f`: the measured incident flux of atmospheric radiation in the PAR, in W m[soil]⁻² (== J m[soil]⁻² s⁻¹)

# Examples

Import the example models defined in the `Examples` sub-module:

```julia
using PlantSimEngine
using PlantSimEngine.Examples
```

Create a model list with a Beer model, and fit it to the data:

```julia
m = ModelList(Beer(0.6), status=(LAI=2.0,))
meteo = Atmosphere(T=20.0, Wind=1.0, P=101.3, Rh=0.65, Ri_PAR_f=300.0)
run!(m, meteo)
df = DataFrame(aPPFD=m[:aPPFD][1], LAI=m.status.LAI[1], Ri_PAR_f=meteo.Ri_PAR_f[1])
fit(Beer, df)
```
