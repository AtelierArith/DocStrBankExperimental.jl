High-level wrapper for VkSamplerYcbcrConversionCreateInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSamplerYcbcrConversionCreateInfo.html)

```julia
struct SamplerYcbcrConversionCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `format::Vulkan.Format`
  * `ycbcr_model::Vulkan.SamplerYcbcrModelConversion`
  * `ycbcr_range::Vulkan.SamplerYcbcrRange`
  * `components::Vulkan.ComponentMapping`
  * `x_chroma_offset::Vulkan.ChromaLocation`
  * `y_chroma_offset::Vulkan.ChromaLocation`
  * `chroma_filter::Vulkan.Filter`
  * `force_explicit_reconstruction::Bool`
