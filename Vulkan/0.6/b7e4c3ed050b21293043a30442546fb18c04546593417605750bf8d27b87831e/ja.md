High-level wrapper for VkDisplayPropertiesKHR.

Extension: VK*KHR*display

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPropertiesKHR.html)

```julia
struct DisplayPropertiesKHR <: Vulkan.HighLevelStruct
```

  * `display::Vulkan.DisplayKHR`
  * `display_name::String`
  * `physical_dimensions::Vulkan.Extent2D`
  * `physical_resolution::Vulkan.Extent2D`
  * `supported_transforms::Vulkan.SurfaceTransformFlagKHR`
  * `plane_reorder_possible::Bool`
  * `persistent_content::Bool`
