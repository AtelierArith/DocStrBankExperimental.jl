High-level wrapper for VkLayerProperties.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkLayerProperties.html)

```julia
struct LayerProperties <: Vulkan.HighLevelStruct
```

  * `layer_name::String`
  * `spec_version::VersionNumber`
  * `implementation_version::VersionNumber`
  * `description::String`
