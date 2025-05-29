```
constraints_data(m, n::Node, 𝒯, 𝒫, modeltype::EnergyModel, data::EmissionsEnergy)
constraints_data(m, n::Node, 𝒯, 𝒫, modeltype::EnergyModel, data::EmissionsProcess)
constraints_data(m, n::Node, 𝒯, 𝒫, modeltype::EnergyModel, data::CaptureEnergyEmissions)
constraints_data(m, n::Node, 𝒯, 𝒫, modeltype::EnergyModel, data::CaptureProcessEmissions)
constraints_data(m, n::Node, 𝒯, 𝒫, modeltype::EnergyModel, data::CaptureProcessEnergyEmissions)
```

プロセスにおける排出量と捕集されたCO₂の量を計算するための制約関数。データが[`CaptureData`](@ref)である場合、CO₂の変数:flow_outに対する制約を提供します。

いくつかの構成が存在します：

  * **[`EmissionsEnergy`](@ref)** はエネルギー使用に関連する排出量のみを対応します。
  * **[`EmissionsProcess`](@ref)** はプロセスとエネルギー使用に関連する排出量の両方に対応します。
  * **[`CaptureEnergyEmissions`](@ref)** はエネルギー使用に関連する排出量の捕集に対応し、プロセス排出量を含むことができます。
  * **[`CaptureProcessEmissions`](@ref)** はエネルギー使用に関連する排出量が捕集されない間のプロセス排出量の捕集に対応します。
  * **[`CaptureProcessEnergyEmissions`](@ref)** はプロセスとエネルギー使用に関連する排出量の両方の捕集に対応します。
