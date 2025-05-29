Extension: VK_KHR_deferred_host_operations

Arguments:

  * `device::Device`
  * `operation::DeferredOperationKHR` (externsync)
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyDeferredOperationKHR.html)

```julia
_destroy_deferred_operation_khr(
    device,
    operation;
    allocator
)

```
