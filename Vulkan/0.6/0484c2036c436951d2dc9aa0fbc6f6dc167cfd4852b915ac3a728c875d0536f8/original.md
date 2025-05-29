High-level wrapper for VkDeviceGroupRenderPassBeginInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupRenderPassBeginInfo.html)

```julia
struct DeviceGroupRenderPassBeginInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `device_mask::UInt32`
  * `device_render_areas::Vector{Vulkan.Rect2D}`
