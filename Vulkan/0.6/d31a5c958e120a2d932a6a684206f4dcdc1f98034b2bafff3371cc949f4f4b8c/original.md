Arguments:

  * `src_buffer::Buffer`
  * `dst_buffer::Buffer`
  * `regions::Vector{_BufferCopy2}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyBufferInfo2.html)

```julia
_CopyBufferInfo2(
    src_buffer,
    dst_buffer,
    regions::AbstractArray;
    next
) -> Vulkan._CopyBufferInfo2

```
