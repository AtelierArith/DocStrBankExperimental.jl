High-level wrapper for VkPhysicalDeviceToolProperties.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceToolProperties.html)

```julia
struct PhysicalDeviceToolProperties <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `name::String`
  * `version::String`
  * `purposes::Vulkan.ToolPurposeFlag`
  * `description::String`
  * `layer::String`
