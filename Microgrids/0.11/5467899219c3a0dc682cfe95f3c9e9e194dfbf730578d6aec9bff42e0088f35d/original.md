```
component_costs(mg_project::Project, lifetime::Real,
    investment::Real, replacement::Real, salvage::Real,
    om_annual::Real, fuel_annual::Real,
    salvage_type::SalvageType=LinearSalvage)
```

Compute net present cost factors of a component over the Microgrid lifetime.

Cost evaluation is done from nominal and annual cost factors.

### Arguments

  * mg_project: microgrid project description (e.g. with discount rate and lifetime)
  * lifetime: effective lifetime of the component
  * investment: initial investment cost
  * replacement: nominal cost for each replacement
  * salvage: nominal salvage value if component is sold at zero aging
  * om_annual: nominal operation & maintenance (O&M) cost per year
  * fuel_annual: nominal cost of fuel per year
  * salvage_type: choice of formula for salvage value computation, among the possible `SalvageType` enum values (`LinearSalvage` the default, or `ConsistentSalvage`, see `SalvageType` documentation)
