拡張: VK*NV*shading*rate*image

引数:

  * `shading_rate_image::Bool`
  * `shading_rate_coarse_sample_order::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShadingRateImageFeaturesNV.html)

```julia
_PhysicalDeviceShadingRateImageFeaturesNV(
    shading_rate_image::Bool,
    shading_rate_coarse_sample_order::Bool;
    next
) -> Vulkan._PhysicalDeviceShadingRateImageFeaturesNV

```
