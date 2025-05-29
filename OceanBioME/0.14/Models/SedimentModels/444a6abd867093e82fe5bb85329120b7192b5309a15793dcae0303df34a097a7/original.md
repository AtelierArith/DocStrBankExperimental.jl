```
SimpleMultiGSediment(grid;
                     fast_decay_rate = 2/day,
                     slow_decay_rate = 0.2/day,
                     fast_redfield = 0.1509,
                     slow_redfield = 0.13,
                     fast_fraction = 0.74,
                     slow_fraction = 0.26,
                     refactory_fraction = 0.1,
                     sedimentation_rate = 982 * abs(znode(1, 1, 1, grid, Center(), Center(), Center())) ^ (-1.548), # cm/year, incorrect for D < 100m
                     anoxia_half_saturation = 1.0, # mmol/m³ (arbitarily low)
                     nitrate_oxidation_params = on_architecture(architecture(grid), (- 1.9785, 0.2261, -0.0615, -0.0289, - 0.36109, - 0.0232)),
                     denitrification_params = on_architecture(architecture(grid), (- 3.0790, 1.7509, 0.0593, - 0.1923, 0.0604, 0.0662)),
                     anoxic_params = on_architecture(architecture(grid), (- 3.9476, 2.6269, - 0.2426, -1.3349, 0.1826, - 0.0143)),
                     solid_dep_params = on_architecture(architecture(grid), (0.233, 0.336, 982.0, - 1.548)),
                     sinking_nitrogen = (:sPOM, :bPOM),
                     sinking_carbon = nothing,
                     sinking_redfield = ifelse(isnothing(sinking_carbon), convert(eltype(grid), 6.56), nothing),
                     kwargs...)
```

Return a single-layer "multi G" sediment model (`SimpleMultiG`) on `grid`, where parameters can be optionally specified.

The model is a single layer (i.e. does not include porous diffusion) model with three classes of sediment organic matter which decay at three different rates (fast, slow, refactory). The nitrification/denitrification/anoxic mineralisation fractions default to the parameterisation of Soetaert et al. 2000; doi:[10.1016/S0012-8252(00)00004-0](https://doi.org/10.1016/S0012-8252(00)00004-0).

This model has not yet been validated or compared to observational data. The variety of degridation processes is likely to be strongly dependent on oxygen availability (see [https://bg.copernicus.org/articles/6/1273/2009/bg-6-1273-2009.pdf](https://bg.copernicus.org/articles/6/1273/2009/bg-6-1273-2009.pdf)) so it will therefore be important to also thoroughly validate the oxygen model (also currently limited).

# Example

```jldoctest simplemultig; filter = r".*@ OceanBioME.Models.Sediments.*"
julia> using OceanBioME, Oceananigans

julia> grid = RectilinearGrid(size=(3, 3, 30), extent=(10, 10, 200));

julia> sediment_model = SimpleMultiGSediment(grid)
`BiogeochemicalSediment` with `Single-layer multi-G sediment model (Float64)` biogeochemsitry
    Prognostic fields: (:Ns, :Nf, :Nr)
    Tracked fields: (:NO₃, :NH₄, :O₂, :sPOM, :bPOM)
    Coupled fields: (:NO₃, :NH₄, :O₂)

julia> biogeochemistry = LOBSTER(; grid, sediment_model)
LOBSTER{Float64} with carbonates ❌, oxygen ❌, variable Redfield ratio ❌ and (:sPOM, :bPOM) sinking
 Light attenuation: Two-band light attenuation model (Float64)
 Sediment: `BiogeochemicalSediment` with `Single-layer multi-G sediment model (Float64)` biogeochemsitry
 Particles: Nothing
 Modifiers: Nothing

```
