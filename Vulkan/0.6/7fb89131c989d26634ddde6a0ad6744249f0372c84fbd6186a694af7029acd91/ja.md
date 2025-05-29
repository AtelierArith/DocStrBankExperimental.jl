引数:

  * `memory::DeviceMemory`
  * `offset::UInt64`
  * `size::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMappedMemoryRange.html)

```julia
_MappedMemoryRange(
    memory,
    offset::Integer,
    size::Integer;
    next
) -> Vulkan._MappedMemoryRange

```
