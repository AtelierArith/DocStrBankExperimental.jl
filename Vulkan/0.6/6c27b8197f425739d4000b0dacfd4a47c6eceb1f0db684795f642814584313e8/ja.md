引数:

  * `buffer::Buffer`
  * `memory::DeviceMemory`
  * `memory_offset::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindBufferMemoryInfo.html)

```julia
_BindBufferMemoryInfo(
    buffer,
    memory,
    memory_offset::Integer;
    next
) -> Vulkan._BindBufferMemoryInfo

```
