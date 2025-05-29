High-level wrapper for VkCoarseSampleOrderCustomNV.

Extension: VK_NV_shading_rate_image

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCoarseSampleOrderCustomNV.html)

```julia
struct CoarseSampleOrderCustomNV <: Vulkan.HighLevelStruct
```

  * `shading_rate::Vulkan.ShadingRatePaletteEntryNV`
  * `sample_count::UInt32`
  * `sample_locations::Vector{Vulkan.CoarseSampleLocationNV}`
