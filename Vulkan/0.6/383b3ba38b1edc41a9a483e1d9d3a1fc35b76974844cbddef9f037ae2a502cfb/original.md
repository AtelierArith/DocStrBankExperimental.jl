Extension: VK_KHR_deferred_host_operations

Return codes:

  * `SUCCESS`
  * `NOT_READY`

Arguments:

  * `device::Device`
  * `operation::DeferredOperationKHR`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDeferredOperationResultKHR.html)

```julia
get_deferred_operation_result_khr(
    device,
    operation
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
