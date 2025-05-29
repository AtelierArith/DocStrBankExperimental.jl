Arguments:

  * `device::Device`
  * `allocation_size::UInt64`
  * `memory_type_index::UInt32`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkAllocateMemory.html)

```julia
DeviceMemory(
    device,
    allocation_size::Integer,
    memory_type_index::Integer;
    allocator,
    next
) -> Vulkan.DeviceMemory

```
