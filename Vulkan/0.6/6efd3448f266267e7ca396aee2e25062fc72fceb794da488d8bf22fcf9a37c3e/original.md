Arguments:

  * `src_queue_family_index::UInt32`
  * `dst_queue_family_index::UInt32`
  * `buffer::Buffer`
  * `offset::UInt64`
  * `size::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `src_stage_mask::UInt64`: defaults to `0`
  * `src_access_mask::UInt64`: defaults to `0`
  * `dst_stage_mask::UInt64`: defaults to `0`
  * `dst_access_mask::UInt64`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferMemoryBarrier2.html)

```julia
_BufferMemoryBarrier2(
    src_queue_family_index::Integer,
    dst_queue_family_index::Integer,
    buffer,
    offset::Integer,
    size::Integer;
    next,
    src_stage_mask,
    src_access_mask,
    dst_stage_mask,
    dst_access_mask
) -> Vulkan._BufferMemoryBarrier2

```
