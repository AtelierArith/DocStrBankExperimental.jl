Extension: VK_KHR_deferred_host_operations

Return codes:

  * `SUCCESS`
  * `THREAD_DONE_KHR`
  * `THREAD_IDLE_KHR`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `operation::DeferredOperationKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDeferredOperationJoinKHR.html)

```julia
_deferred_operation_join_khr(
    device,
    operation
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
