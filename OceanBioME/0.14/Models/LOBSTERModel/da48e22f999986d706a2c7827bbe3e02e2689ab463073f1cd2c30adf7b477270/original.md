```
LOBSTER(; grid::AbstractGrid{FT},
          phytoplankton_preference::FT = 0.5,
          maximum_grazing_rate::FT = 9.26e-6, # 1/s
          grazing_half_saturation::FT = 1.0, # mmol N/m³
          light_half_saturation::FT = 33.0, # W/m² (?)
          nitrate_ammonia_inhibition::FT = 3.0,
          nitrate_half_saturation::FT = 0.7, # mmol N/m³
          ammonia_half_saturation::FT = 0.001, # mmol N/m³
          maximum_phytoplankton_growthrate::FT = 1.21e-5, # 1/s
          zooplankton_assimilation_fraction::FT = 0.7,
          zooplankton_mortality::FT = 2.31e-6, # 1/s/mmol N/m³
          zooplankton_excretion_rate::FT = 5.8e-7, # 1/s
          phytoplankton_mortality::FT = 5.8e-7, # 1/s
          small_detritus_remineralisation_rate::FT = 5.88e-7, # 1/s
          large_detritus_remineralisation_rate::FT = 5.88e-7, # 1/s
          phytoplankton_exudation_fraction::FT = 0.05,
          nitrification_rate::FT = 5.8e-7, # 1/s
          ammonia_fraction_of_exudate::FT = 0.75, 
          ammonia_fraction_of_excriment::FT = 0.5,
          ammonia_fraction_of_detritus::FT = 0.0,
          phytoplankton_redfield::FT = 6.56, # mol C/mol N
          organic_redfield::FT = 6.56, # mol C/mol N
          phytoplankton_chlorophyll_ratio::FT = 1.31, # g Chl/mol N
          organic_carbon_calcate_ratio::FT = 0.1, # mol CaCO₃/mol C
          respiration_oxygen_nitrogen_ratio::FT = 10.75, # mol O/molN
          nitrification_oxygen_nitrogen_ratio::FT = 2.0, # mol O/molN
          slow_sinking_mortality_fraction::FT = 0.5, 
          fast_sinking_mortality_fraction::FT = 0.5,
          dissolved_organic_breakdown_rate::FT = 3.86e-7, # 1/s
          zooplankton_calcite_dissolution::FT = 0.3,

          surface_photosynthetically_active_radiation = default_surface_PAR,

          light_attenuation_model::LA =
              TwoBandPhotosyntheticallyActiveRadiation(; grid, 
                                                         surface_PAR = surface_photosynthetically_active_radiation),
          sediment_model::S = nothing,

          carbonates::Bool = false,
          oxygen::Bool = false,
          variable_redfield::Bool = false,

          sinking_speeds = (sPOM = 3.47e-5, bPOM = 200/day),
          open_bottom::Bool = true,

          scale_negatives = false,

          particles::P = nothing,
          modifiers::M = nothing)
```

Construct an instance of the [LOBSTER](@ref LOBSTER) biogeochemical model.

# Keyword Arguments

  * `grid`: (required) the geometry to build the model on, required to calculate sinking
  * `phytoplankton_preference`, ..., `dissolved_organic_breakdown_rate`: LOBSTER parameter values
  * `surface_photosynthetically_active_radiation`: funciton (or array in the future) for the photosynthetically available radiation at the surface, should be shape `f(x, y, t)`
  * `light_attenuation_model`: light attenuation model which integrated the attenuation of available light
  * `sediment_model`: slot for `BiogeochemicalSediment`
  * `carbonates`, `oxygen`, and `variable_redfield`: include models for carbonate chemistry and/or oxygen chemistry and/or variable redfield ratio dissolved and particulate organic matter
  * `sinking_speed`: named tuple of constant sinking, of fields (i.e. `ZFaceField(...)`) for any tracers which sink (convention is that a sinking speed is positive, but a field will need to follow the usual down being negative)
  * `open_bottom`: should the sinking velocity be smoothly brought to zero at the bottom to prevent the tracers leaving the domain
  * `scale_negatives`: scale negative tracers?
  * `particles`: slot for `BiogeochemicalParticles`
  * `modifiers`: slot for components which modify the biogeochemistry when the tendencies have been calculated or when the state is updated

# Example

```jldoctest
julia> using OceanBioME

julia> using Oceananigans

julia> grid = RectilinearGrid(size=(3, 3, 30), extent=(10, 10, 200));

julia> model = LOBSTER(; grid)
LOBSTER{Float64} with carbonates ❌, oxygen ❌, variable Redfield ratio ❌ and (:sPOM, :bPOM) sinking 
 Light attenuation: Two-band light attenuation model (Float64)
 Sediment: Nothing
 Particles: Nothing
 Modifiers: Nothing
```
