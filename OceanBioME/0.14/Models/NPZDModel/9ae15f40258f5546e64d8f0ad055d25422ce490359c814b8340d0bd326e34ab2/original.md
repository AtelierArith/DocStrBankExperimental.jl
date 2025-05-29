```
NutrientPhytoplanktonZooplanktonDetritus(; grid::AbstractGrid{FT},
                                           initial_photosynthetic_slope::FT = 0.1953 / day, # 1/(W/m²)/s
                                           base_maximum_growth::FT = 0.6989 / day, # 1/s
                                           nutrient_half_saturation::FT = 2.3868, # mmol N/m³
                                           base_respiration_rate::FT = 0.066 / day, # 1/s/(mmol N / m³)
                                           phyto_base_mortality_rate::FT = 0.0101 / day, # 1/s/(mmol N / m³)
                                           maximum_grazing_rate::FT = 2.1522 / day, # 1/s
                                           grazing_half_saturation::FT = 0.5573, # mmol N/m³
                                           assimulation_efficiency::FT = 0.9116, 
                                           base_excretion_rate::FT = 0.0102 / day, # 1/s/(mmol N / m³)
                                           zoo_base_mortality_rate::FT = 0.3395 / day, # 1/s/(mmol N / m³)²
                                           remineralization_rate::FT = 0.1213 / day, # 1/s

                                           surface_photosynthetically_active_radiation = default_surface_PAR,
                                           light_attenuation_model::LA =
                                               TwoBandPhotosyntheticallyActiveRadiation(; grid,
                                                                                          surface_PAR = surface_photosynthetically_active_radiation),
                                           sediment_model::S = nothing,
            
                                           sinking_speeds = (P = 0.2551/day, D = 2.7489/day),
                                           open_bottom::Bool = true,

                                           scale_negatives = false,
                                                                                  
                                           particles::P = nothing,
                                           modifiers::M = nothing)
```

Construct a Nutrient-Phytoplankton-Zooplankton-Detritus ([NPZD](@ref NPZD)) biogeochemical model.

# Keyword Arguments

  * `grid`: (required) the geometry to build the model on, required to calculate sinking
  * `initial_photosynthetic_slope`, ..., `remineralization_rate`: NPZD parameter values
  * `surface_photosynthetically_active_radiation`: function (or array in the future) for the photosynthetically available radiation at the surface, should be shape `f(x, y, t)`
  * `light_attenuation_model`: light attenuation model which integrated the attenuation of available light
  * `sediment_model`: slot for `BiogeochemicalSediment`
  * `sinking_speed`: named tuple of constant sinking, of fields (i.e. `ZFaceField(...)`) for any tracers which sink (convention is that a sinking speed is positive, but a field will need to follow the usual down being negative)
  * `open_bottom`: should the sinking velocity be smoothly brought to zero at the bottom to prevent the tracers leaving the domain
  * `scale_negatives`: scale negative tracers?
  * `particles`: slot for `BiogeochemicalParticles`
  * `modifiers`: slot for components which modify the biogeochemistry when the tendencies have been calculated or when the state is updated

# Example

```jldoctest
julia> using OceanBioME

julia> using Oceananigans

julia> grid = RectilinearGrid(size=(20, 30), extent=(200, 200), topology=(Bounded, Flat, Bounded));

julia> model = NutrientPhytoplanktonZooplanktonDetritus(; grid)
NutrientPhytoplanktonZooplanktonDetritus{Float64} model, with (:P, :D) sinking 
 Light attenuation: Two-band light attenuation model (Float64)
 Sediment: Nothing
 Particles: Nothing
 Modifiers: Nothing
```
