拡張: VK*KHR*deferred*host*operations

戻り値コード:

  * `SUCCESS`
  * `NOT_READY`

引数:

  * `device::Device`
  * `operation::DeferredOperationKHR`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetDeferredOperationResultKHR.html)

```julia
_get_deferred_operation_result_khr(
    device,
    operation
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
