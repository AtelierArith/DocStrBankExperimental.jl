Extension: VK_NV_shading_rate_image

Arguments:

  * `shading_rate_image_enable::Bool`
  * `shading_rate_palettes::Vector{_ShadingRatePaletteNV}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportShadingRateImageStateCreateInfoNV.html)

```julia
_PipelineViewportShadingRateImageStateCreateInfoNV(
    shading_rate_image_enable::Bool,
    shading_rate_palettes::AbstractArray;
    next
) -> Vulkan._PipelineViewportShadingRateImageStateCreateInfoNV

```
