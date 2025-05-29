拡張: VK*KHR*deferred*host*operations

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

引数:

  * `device::Device`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDeferredOperationKHR.html)

```julia
_create_deferred_operation_khr(
    device;
    allocator
) -> ResultTypes.Result{Vulkan.DeferredOperationKHR, Vulkan.VulkanError}

```
