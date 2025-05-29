引数:

  * `device::Device`
  * `allocation_size::UInt64`
  * `memory_type_index::UInt32`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkAllocateMemory.html)

```julia
DeviceMemory(
    device,
    allocation_size::Integer,
    memory_type_index::Integer;
    allocator,
    next
) -> Vulkan.DeviceMemory

```
