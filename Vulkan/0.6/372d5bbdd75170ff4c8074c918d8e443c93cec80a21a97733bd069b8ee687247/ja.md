SPIR-Vの機能と、それを有効にするために考慮すべきさまざまな要件に関する情報。

```julia
struct SpecCapabilitySPIRV
```

  * `name::Symbol`: SPIR-V機能の名前。
  * `promoted_to::Union{Nothing, VersionNumber}`: SPIR-V機能が昇格されたVulkan APIのコアバージョン（昇格された場合）。
  * `enabling_extensions::Vector{String}`: SPIR-V機能を暗黙的に有効にするVulkan拡張。
  * `enabling_features::Vector{Vulkan.FeatureCondition}`: SPIR-V機能を暗黙的に有効にするVulkan機能。
  * `enabling_properties::Vector{Vulkan.PropertyCondition}`: SPIR-V機能を暗黙的に有効にするVulkanプロパティ。
