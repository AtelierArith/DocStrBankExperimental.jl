拡張: VK*NV*shading*rate*image

引数:

  * `shading_rate_image_enable::Bool`
  * `shading_rate_palettes::Vector{_ShadingRatePaletteNV}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportShadingRateImageStateCreateInfoNV.html)

```julia
_PipelineViewportShadingRateImageStateCreateInfoNV(
    shading_rate_image_enable::Bool,
    shading_rate_palettes::AbstractArray;
    next
) -> Vulkan._PipelineViewportShadingRateImageStateCreateInfoNV

```
