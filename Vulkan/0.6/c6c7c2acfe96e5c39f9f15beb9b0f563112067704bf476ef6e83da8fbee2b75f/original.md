High-level wrapper for VkRectLayerKHR.

Extension: VK_KHR_incremental_present

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRectLayerKHR.html)

```julia
struct RectLayerKHR <: Vulkan.HighLevelStruct
```

  * `offset::Vulkan.Offset2D`
  * `extent::Vulkan.Extent2D`
  * `layer::UInt32`
