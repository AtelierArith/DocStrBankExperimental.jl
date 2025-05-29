拡張: VK*KHR*deferred*host*operations

戻りコード:

  * `SUCCESS`
  * `THREAD_DONE_KHR`
  * `THREAD_IDLE_KHR`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `operation::DeferredOperationKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDeferredOperationJoinKHR.html)

```julia
_deferred_operation_join_khr(
    device,
    operation
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
