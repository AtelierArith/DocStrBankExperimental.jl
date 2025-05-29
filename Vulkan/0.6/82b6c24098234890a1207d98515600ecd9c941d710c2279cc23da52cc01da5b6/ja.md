VkSurfacePresentScalingCapabilitiesEXTの高レベルラッパー。

拡張: VK*EXT*surface_maintenance1

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfacePresentScalingCapabilitiesEXT.html)

```julia
struct SurfacePresentScalingCapabilitiesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `supported_present_scaling::Vulkan.PresentScalingFlagEXT`
  * `supported_present_gravity_x::Vulkan.PresentGravityFlagEXT`
  * `supported_present_gravity_y::Vulkan.PresentGravityFlagEXT`
  * `min_scaled_image_extent::Union{Ptr{Nothing}, Vulkan.Extent2D}`
  * `max_scaled_image_extent::Union{Ptr{Nothing}, Vulkan.Extent2D}`
