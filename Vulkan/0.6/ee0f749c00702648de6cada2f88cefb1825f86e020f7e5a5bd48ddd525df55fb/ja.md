引数:

  * `device::Device`
  * `format::Format`
  * `ycbcr_model::SamplerYcbcrModelConversion`
  * `ycbcr_range::SamplerYcbcrRange`
  * `components::_ComponentMapping`
  * `x_chroma_offset::ChromaLocation`
  * `y_chroma_offset::ChromaLocation`
  * `chroma_filter::Filter`
  * `force_explicit_reconstruction::Bool`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateSamplerYcbcrConversion.html)

```julia
SamplerYcbcrConversion(
    device,
    format::Vulkan.Format,
    ycbcr_model::Vulkan.SamplerYcbcrModelConversion,
    ycbcr_range::Vulkan.SamplerYcbcrRange,
    components::Vulkan._ComponentMapping,
    x_chroma_offset::Vulkan.ChromaLocation,
    y_chroma_offset::Vulkan.ChromaLocation,
    chroma_filter::Vulkan.Filter,
    force_explicit_reconstruction::Bool;
    allocator,
    next
) -> Vulkan.SamplerYcbcrConversion

```
