High-level wrapper for VkDisplaySurfaceCreateInfoKHR.

Extension: VK_KHR_display

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplaySurfaceCreateInfoKHR.html)

```julia
struct DisplaySurfaceCreateInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `display_mode::Vulkan.DisplayModeKHR`
  * `plane_index::UInt32`
  * `plane_stack_index::UInt32`
  * `transform::Vulkan.SurfaceTransformFlagKHR`
  * `global_alpha::Float32`
  * `alpha_mode::Vulkan.DisplayPlaneAlphaFlagKHR`
  * `image_extent::Vulkan.Extent2D`
