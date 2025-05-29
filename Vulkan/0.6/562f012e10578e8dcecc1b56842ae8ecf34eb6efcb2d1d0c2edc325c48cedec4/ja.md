引数:

  * `dst_set::DescriptorSet`
  * `dst_binding::UInt32`
  * `dst_array_element::UInt32`
  * `descriptor_type::DescriptorType`
  * `image_info::Vector{_DescriptorImageInfo}`
  * `buffer_info::Vector{_DescriptorBufferInfo}`
  * `texel_buffer_view::Vector{BufferView}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `descriptor_count::UInt32`: デフォルトは `max(pointer_length(image_info), pointer_length(buffer_info), pointer_length(texel_buffer_view))`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkWriteDescriptorSet.html)

```julia
_WriteDescriptorSet(
    dst_set,
    dst_binding::Integer,
    dst_array_element::Integer,
    descriptor_type::Vulkan.DescriptorType,
    image_info::AbstractArray,
    buffer_info::AbstractArray,
    texel_buffer_view::AbstractArray;
    next,
    descriptor_count
) -> Vulkan._WriteDescriptorSet

```
