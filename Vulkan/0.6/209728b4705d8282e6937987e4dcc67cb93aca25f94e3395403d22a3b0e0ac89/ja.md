拡張: VK*KHR*acceleration_structure

戻り値コード:

  * `SUCCESS`
  * `OPERATION_DEFERRED_KHR`
  * `OPERATION_NOT_DEFERRED_KHR`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `info::_CopyAccelerationStructureInfoKHR`
  * `deferred_operation::DeferredOperationKHR`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCopyAccelerationStructureKHR.html)

```julia
_copy_acceleration_structure_khr(
    device,
    info::Vulkan._CopyAccelerationStructureInfoKHR;
    deferred_operation
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
