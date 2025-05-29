返却コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_EXTERNAL_HANDLE`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

引数:

  * `device::Device`
  * `allocation_size::UInt64`
  * `memory_type_index::UInt32`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkAllocateMemory.html)

```julia
allocate_memory(
    device,
    allocation_size::Integer,
    memory_type_index::Integer;
    allocator,
    next
) -> ResultTypes.Result{Vulkan.DeviceMemory, Vulkan.VulkanError}

```
