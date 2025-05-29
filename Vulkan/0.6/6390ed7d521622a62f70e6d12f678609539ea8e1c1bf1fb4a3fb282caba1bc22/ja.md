引数:

  * `src_buffer::Buffer`
  * `dst_buffer::Buffer`
  * `regions::Vector{BufferCopy2}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyBufferInfo2.html)

```julia
CopyBufferInfo2(
    src_buffer::Vulkan.Buffer,
    dst_buffer::Vulkan.Buffer,
    regions::AbstractArray;
    next
) -> Vulkan.CopyBufferInfo2

```
