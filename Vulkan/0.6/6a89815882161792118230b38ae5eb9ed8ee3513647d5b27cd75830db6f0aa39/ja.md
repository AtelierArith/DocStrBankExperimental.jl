拡張: VK*NV*shading*rate*image

引数:

  * `shading_rate_texel_size::Extent2D`
  * `shading_rate_palette_size::UInt32`
  * `shading_rate_max_coarse_samples::UInt32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShadingRateImagePropertiesNV.html)

```julia
PhysicalDeviceShadingRateImagePropertiesNV(
    shading_rate_texel_size::Vulkan.Extent2D,
    shading_rate_palette_size::Integer,
    shading_rate_max_coarse_samples::Integer;
    next
) -> Vulkan.PhysicalDeviceShadingRateImagePropertiesNV

```
