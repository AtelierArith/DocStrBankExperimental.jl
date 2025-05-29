High-level wrapper for VkDeviceImageMemoryRequirements.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceImageMemoryRequirements.html)

```julia
struct DeviceImageMemoryRequirements <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `create_info::Vulkan.ImageCreateInfo`
  * `plane_aspect::Vulkan.ImageAspectFlag`
