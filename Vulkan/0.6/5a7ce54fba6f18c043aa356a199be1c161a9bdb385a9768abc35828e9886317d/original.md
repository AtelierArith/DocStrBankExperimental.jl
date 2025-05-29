Arguments:

  * `allocation_size::UInt64`
  * `memory_type_index::UInt32`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryAllocateInfo.html)

```julia
MemoryAllocateInfo(
    allocation_size::Integer,
    memory_type_index::Integer;
    next
) -> Vulkan.MemoryAllocateInfo

```
