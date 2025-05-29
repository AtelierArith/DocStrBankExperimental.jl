High-level wrapper for VkPhysicalDeviceShadingRateImagePropertiesNV.

Extension: VK_NV_shading_rate_image

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShadingRateImagePropertiesNV.html)

```julia
struct PhysicalDeviceShadingRateImagePropertiesNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `shading_rate_texel_size::Vulkan.Extent2D`
  * `shading_rate_palette_size::UInt32`
  * `shading_rate_max_coarse_samples::UInt32`
