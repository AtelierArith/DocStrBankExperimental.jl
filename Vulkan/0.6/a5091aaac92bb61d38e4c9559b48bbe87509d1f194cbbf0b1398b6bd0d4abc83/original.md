Arguments:

  * `memory::DeviceMemory`
  * `offset::UInt64`
  * `size::UInt64`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMappedMemoryRange.html)

```julia
MappedMemoryRange(
    memory::Vulkan.DeviceMemory,
    offset::Integer,
    size::Integer;
    next
) -> Vulkan.MappedMemoryRange

```
