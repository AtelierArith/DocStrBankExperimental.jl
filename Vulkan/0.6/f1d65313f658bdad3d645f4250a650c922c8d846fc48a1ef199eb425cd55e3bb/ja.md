SPIR-V拡張は、コアバージョンに昇格されたか、または有効なVulkan拡張によって暗黙的に有効にされる可能性があります。

```julia
struct SpecExtensionSPIRV
```

  * `name::String`: SPIR-V拡張の名前。
  * `promoted_to::Union{Nothing, VersionNumber}`: 拡張が昇格された場合の、Vulkan APIのコアバージョン。
  * `enabling_extensions::Vector{String}`: SPIR-V拡張を暗黙的に有効にするVulkan拡張。
