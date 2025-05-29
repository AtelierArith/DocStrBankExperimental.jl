Arguments:

  * `memory::DeviceMemory`
  * `offset::UInt64`
  * `size::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMappedMemoryRange.html)

```julia
_MappedMemoryRange(
    memory,
    offset::Integer,
    size::Integer;
    next
) -> Vulkan._MappedMemoryRange

```
