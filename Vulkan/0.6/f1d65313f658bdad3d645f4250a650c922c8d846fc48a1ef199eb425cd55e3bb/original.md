SPIR-V extension which may have been promoted to a core version or be enabled implicitly by enabled Vulkan extensions.

```julia
struct SpecExtensionSPIRV
```

  * `name::String`: Name of the SPIR-V extension.
  * `promoted_to::Union{Nothing, VersionNumber}`: Core version of the Vulkan API in which the extension was promoted, if promoted.
  * `enabling_extensions::Vector{String}`: Vulkan extensions that implicitly enable the SPIR-V extension.
