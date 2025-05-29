Extension: VK_NV_shading_rate_image

Arguments:

  * `shading_rate::ShadingRatePaletteEntryNV`
  * `sample_count::UInt32`
  * `sample_locations::Vector{_CoarseSampleLocationNV}`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCoarseSampleOrderCustomNV.html)

```julia
_CoarseSampleOrderCustomNV(
    shading_rate::Vulkan.ShadingRatePaletteEntryNV,
    sample_count::Integer,
    sample_locations::AbstractArray
) -> Vulkan._CoarseSampleOrderCustomNV

```
