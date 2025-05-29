引数:

  * `memory::DeviceMemory`
  * `offset::UInt64`
  * `size::UInt64`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMappedMemoryRange.html)

```julia
MappedMemoryRange(
    memory::Vulkan.DeviceMemory,
    offset::Integer,
    size::Integer;
    next
) -> Vulkan.MappedMemoryRange

```
