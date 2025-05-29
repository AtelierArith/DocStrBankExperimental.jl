Arguments:

  * `src_access_mask::AccessFlag`
  * `dst_access_mask::AccessFlag`
  * `src_queue_family_index::UInt32`
  * `dst_queue_family_index::UInt32`
  * `buffer::Buffer`
  * `offset::UInt64`
  * `size::UInt64`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferMemoryBarrier.html)

```julia
BufferMemoryBarrier(
    src_access_mask::Vulkan.AccessFlag,
    dst_access_mask::Vulkan.AccessFlag,
    src_queue_family_index::Integer,
    dst_queue_family_index::Integer,
    buffer::Vulkan.Buffer,
    offset::Integer,
    size::Integer;
    next
) -> Vulkan.BufferMemoryBarrier

```
