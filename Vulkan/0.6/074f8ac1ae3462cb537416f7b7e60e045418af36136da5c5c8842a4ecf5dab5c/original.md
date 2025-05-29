Arguments:

  * `src_offset::UInt64`
  * `dst_offset::UInt64`
  * `size::UInt64`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferCopy2.html)

```julia
BufferCopy2(
    src_offset::Integer,
    dst_offset::Integer,
    size::Integer;
    next
) -> Vulkan.BufferCopy2

```
