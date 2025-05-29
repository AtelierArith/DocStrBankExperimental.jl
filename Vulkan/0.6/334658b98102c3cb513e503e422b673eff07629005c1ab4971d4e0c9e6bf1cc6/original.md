Extension: VK_KHR_deferred_host_operations

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDeferredOperationKHR.html)

```julia
create_deferred_operation_khr(
    device;
    allocator
) -> ResultTypes.Result{Vulkan.DeferredOperationKHR, Vulkan.VulkanError}

```
