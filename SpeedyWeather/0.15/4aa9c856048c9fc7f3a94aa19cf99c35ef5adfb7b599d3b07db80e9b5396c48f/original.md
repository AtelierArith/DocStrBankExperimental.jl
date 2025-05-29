Create a struct `EarthAtmosphere <: AbstractAtmosphere`, with the following physical/chemical characteristics. Keyword arguments are

  * `mol_mass_dry_air::AbstractFloat`: molar mass of dry air [g/mol]
  * `mol_mass_vapour::AbstractFloat`: molar mass of water vapour [g/mol]
  * `heat_capacity::AbstractFloat`: specific heat at constant pressure cₚ [J/K/kg]
  * `R_gas::AbstractFloat`: universal gas constant [J/K/mol]
  * `R_dry::AbstractFloat`: specific gas constant for dry air [J/kg/K]
  * `R_vapour::AbstractFloat`: specific gas constant for water vapour [J/kg/K]
  * `mol_ratio::AbstractFloat`: Ratio of gas constants: dry air / water vapour, often called ε [1]
  * `μ_virt_temp::AbstractFloat`: Virtual temperature Tᵥ calculation, Tᵥ = T(1 + μ*q), humidity q, absolute tempereature T
  * `κ::AbstractFloat`: = R_dry/cₚ, gas const for air over heat capacity
  * `water_density::AbstractFloat`: water density [kg/m³]
  * `latent_heat_condensation::AbstractFloat`: latent heat of condensation [J/kg]
  * `latent_heat_sublimation::AbstractFloat`: latent heat of sublimation [J/kg]
  * `stefan_boltzmann::AbstractFloat`: stefan-Boltzmann constant [W/m²/K⁴]
  * `pres_ref::AbstractFloat`: surface reference pressure [Pa]
  * `temp_ref::AbstractFloat`: surface reference temperature [K]
  * `moist_lapse_rate::AbstractFloat`: reference moist-adiabatic temperature lapse rate [K/m]
  * `dry_lapse_rate::AbstractFloat`: reference dry-adiabatic temperature lapse rate [K/m]
  * `layer_thickness::AbstractFloat`: layer thickness for the shallow water model [m]
