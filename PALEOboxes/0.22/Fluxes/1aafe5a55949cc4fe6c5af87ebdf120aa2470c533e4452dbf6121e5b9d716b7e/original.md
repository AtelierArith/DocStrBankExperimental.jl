```
Fluxes
```

Create and manage collections of Target and Contrib Variables used to define fluxes within or between Domains.

# Conventions for defining biogeochemical fluxes within Domains

  * Particulate organic matter (including CaCO3) with stoichiometry Corg:N:P:Ccarb is usually transferred as: `flux_list` `["P", "N", "Corg::CIsotope", "Ccarb::CIsotope"]` with a prefix indicating the function (eg `export_`).
  * Solute fluxes are usually transferred as: `flux_list`  `["DIC::CIsotope", "TAlk", "Ca", "P", "O2", "SO4::SIsotope", "H2S::SIsotope", "CH4::CIsotope"]` (where these names match the Reservoir names for the solutes), with a prefix indicating the function (usually just `flux_` or `soluteflux_`).

# Conventions for defining global fluxes between modules

The model configuration `.yaml` file should create  a `Domain` for each global flux, containing one or more [`Fluxes.ReactionFluxTarget`](@ref).  Fluxes are then transferred (copied) by adding a [`Fluxes.ReactionFluxTransfer`](@ref) to each destination Domain.

Naming conventions for Earth system fluxes:

| Domain name           | target prefix    | flux_list (illustrative, add as needed)                                                              |
|:--------------------- |:---------------- |:---------------------------------------------------------------------------------------------------- |
| fluxAtoLand           | flux_            | ["CO2::CIsotope", "O2"]                                                                              |
| fluxRtoOcean          | flux_            | ["DIC::CIsotope", "TAlk", "Ca", "P", "SO4::SIsotope"]                                                |
| fluxOceanBurial       | flux_            | ["Corg::CIsotope", "Ccarb::CIsotope", "Porg", "Pauth", "PFe", "P", "GYP::SIsotope", "PYR::SIsotope"] |
| fluxSedCrusttoAOcean  | flux_            | ["C::CIsotope", "S::SIsotope", "Redox"]                                                              |
| fluxLandtoSedCrust    | flux_            | ["Ccarb::CIsotope", "Corg::CIsotope", "GYP::SIsotope", "PYR::SIsotope"]                              |
| fluxOceanfloor        | particulateflux_ | ["P", "N", "Corg::CIsotope", "Ccarb::CIsotope"]                                                      |
|                       | soluteflux_      | ["DIC::CIsotope", "TAlk", "Ca", "P", "O2", "SO4::SIsotope", "H2S::SIsotope", "CH4::CIsotope"]        |
| fluxAtmtoOceansurface | flux_            | ["CO2::CIsotope", "CH4::CIsotope", "O2"]                                                             |
