Extension: VK_KHR_deferred_host_operations

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDeferredOperationKHR.html)

```julia
_create_deferred_operation_khr(
    device;
    allocator
) -> ResultTypes.Result{Vulkan.DeferredOperationKHR, Vulkan.VulkanError}

```
