```
run!(::Beer, object, meteo, constants=Constants(), extra=nothing)
```

Computes the photosynthetic photon flux density (`aPPFD`, µmol m⁻² s⁻¹) absorbed by an  object using the incoming PAR radiation flux (`Ri_PAR_f`, W m⁻²) and the Beer-Lambert law of light extinction.

# Arguments

  * `::Beer`: a Beer model, from the model list (*i.e.* m.light_interception)
  * `models`: A `ModelList` struct holding the parameters for the model with

initialisations for `LAI` (m² m⁻²): the leaf area index.

  * `status`: the status of the model, usually the model list status (*i.e.* m.status)
  * `meteo`: meteorology structure, see [`Atmosphere`](https://palmstudio.github.io/PlantMeteo.jl/stable/#PlantMeteo.Atmosphere)
  * `constants = PlantMeteo.Constants()`: physical constants. See `PlantMeteo.Constants` for more details
  * `extra = nothing`: extra arguments, not used here.

# Examples

```julia
m = ModelList(Beer(0.5), status=(LAI=2.0,))

meteo = Atmosphere(T=20.0, Wind=1.0, P=101.3, Rh=0.65, Ri_PAR_q=300.0)

run!(m, meteo)

m[:aPPFD]
```
