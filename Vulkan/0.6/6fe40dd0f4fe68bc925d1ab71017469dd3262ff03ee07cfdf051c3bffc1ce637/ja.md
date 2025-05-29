引数:

  * `format::Format`
  * `ycbcr_model::SamplerYcbcrModelConversion`
  * `ycbcr_range::SamplerYcbcrRange`
  * `components::ComponentMapping`
  * `x_chroma_offset::ChromaLocation`
  * `y_chroma_offset::ChromaLocation`
  * `chroma_filter::Filter`
  * `force_explicit_reconstruction::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSamplerYcbcrConversionCreateInfo.html)

```julia
SamplerYcbcrConversionCreateInfo(
    format::Vulkan.Format,
    ycbcr_model::Vulkan.SamplerYcbcrModelConversion,
    ycbcr_range::Vulkan.SamplerYcbcrRange,
    components::Vulkan.ComponentMapping,
    x_chroma_offset::Vulkan.ChromaLocation,
    y_chroma_offset::Vulkan.ChromaLocation,
    chroma_filter::Vulkan.Filter,
    force_explicit_reconstruction::Bool;
    next
) -> Vulkan.SamplerYcbcrConversionCreateInfo

```
