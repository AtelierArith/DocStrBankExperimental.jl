Extension: VK_NV_shading_rate_image

Arguments:

  * `shading_rate_texel_size::_Extent2D`
  * `shading_rate_palette_size::UInt32`
  * `shading_rate_max_coarse_samples::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShadingRateImagePropertiesNV.html)

```julia
_PhysicalDeviceShadingRateImagePropertiesNV(
    shading_rate_texel_size::Vulkan._Extent2D,
    shading_rate_palette_size::Integer,
    shading_rate_max_coarse_samples::Integer;
    next
) -> Vulkan._PhysicalDeviceShadingRateImagePropertiesNV

```
