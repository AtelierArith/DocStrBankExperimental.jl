Arguments:

  * `src_set::DescriptorSet`
  * `src_binding::UInt32`
  * `src_array_element::UInt32`
  * `dst_set::DescriptorSet`
  * `dst_binding::UInt32`
  * `dst_array_element::UInt32`
  * `descriptor_count::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyDescriptorSet.html)

```julia
_CopyDescriptorSet(
    src_set,
    src_binding::Integer,
    src_array_element::Integer,
    dst_set,
    dst_binding::Integer,
    dst_array_element::Integer,
    descriptor_count::Integer;
    next
) -> Vulkan._CopyDescriptorSet

```
