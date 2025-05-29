Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_EXTERNAL_HANDLE`
  * `ERROR_INVALID_OPAQUE_CAPTURE_ADDRESS_KHR`

Arguments:

  * `device::Device`
  * `allocate_info::MemoryAllocateInfo`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkAllocateMemory.html)

```julia
allocate_memory(
    device,
    allocate_info::Vulkan.MemoryAllocateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.DeviceMemory, Vulkan.VulkanError}

```
