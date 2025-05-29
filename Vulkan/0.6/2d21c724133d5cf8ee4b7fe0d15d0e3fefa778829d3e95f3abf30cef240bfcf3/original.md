Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `format::Format`
  * `ycbcr_model::SamplerYcbcrModelConversion`
  * `ycbcr_range::SamplerYcbcrRange`
  * `components::_ComponentMapping`
  * `x_chroma_offset::ChromaLocation`
  * `y_chroma_offset::ChromaLocation`
  * `chroma_filter::Filter`
  * `force_explicit_reconstruction::Bool`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateSamplerYcbcrConversion.html)

```julia
_create_sampler_ycbcr_conversion(
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
) -> ResultTypes.Result{Vulkan.SamplerYcbcrConversion, Vulkan.VulkanError}

```
