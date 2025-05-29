```
constraints_data(m, n::Node, 𝒯, 𝒫, modeltype::EnergyModel, data::EmissionsEnergy)
constraints_data(m, n::Node, 𝒯, 𝒫, modeltype::EnergyModel, data::EmissionsProcess)
constraints_data(m, n::Node, 𝒯, 𝒫, modeltype::EnergyModel, data::CaptureEnergyEmissions)
constraints_data(m, n::Node, 𝒯, 𝒫, modeltype::EnergyModel, data::CaptureProcessEmissions)
constraints_data(m, n::Node, 𝒯, 𝒫, modeltype::EnergyModel, data::CaptureProcessEnergyEmissions)
```

Constraints functions for calculating both the emissions and amount of CO₂ captured in the process. If the data ia a [`CaptureData`](@ref), it provides the constraint for the variable :flow_out of CO₂.

There exist several configurations:

  * **[`EmissionsEnergy`](@ref)** corresponds to only energy usage related emissions.
  * **[`EmissionsProcess`](@ref)** corresponds to both process and energy usage related emissions.
  * **[`CaptureEnergyEmissions`](@ref)** corresponds to capture of energy usage related emissions, can include process emissions.
  * **[`CaptureProcessEmissions`](@ref)** corresponds to capture of process emissions while energy usage related emissions are not captured.
  * **[`CaptureProcessEnergyEmissions`](@ref)** corresponds to capture of both process and energy  usage related emissions.
