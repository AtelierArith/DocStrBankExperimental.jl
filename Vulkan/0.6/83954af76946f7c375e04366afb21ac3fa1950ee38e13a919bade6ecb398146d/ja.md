返却コード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_EXTERNAL_HANDLE`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

引数:

  * `device::Device`
  * `allocate_info::_MemoryAllocateInfo`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkAllocateMemory.html)

```julia
_allocate_memory(
    device,
    allocate_info::Vulkan._MemoryAllocateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.DeviceMemory, Vulkan.VulkanError}

```
