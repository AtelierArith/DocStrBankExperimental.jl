Arguments:

  * `format_properties::_SparseImageFormatProperties`
  * `image_mip_tail_first_lod::UInt32`
  * `image_mip_tail_size::UInt64`
  * `image_mip_tail_offset::UInt64`
  * `image_mip_tail_stride::UInt64`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseImageMemoryRequirements.html)

```julia
_SparseImageMemoryRequirements(
    format_properties::Vulkan._SparseImageFormatProperties,
    image_mip_tail_first_lod::Integer,
    image_mip_tail_size::Integer,
    image_mip_tail_offset::Integer,
    image_mip_tail_stride::Integer
) -> Vulkan._SparseImageMemoryRequirements

```
