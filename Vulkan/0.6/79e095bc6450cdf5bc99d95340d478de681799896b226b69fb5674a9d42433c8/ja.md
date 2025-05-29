拡張: VK*KHR*acceleration_structure

戻りコード:

  * `SUCCESS`
  * `OPERATION_DEFERRED_KHR`
  * `OPERATION_NOT_DEFERRED_KHR`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `info::_CopyAccelerationStructureToMemoryInfoKHR`
  * `deferred_operation::DeferredOperationKHR`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCopyAccelerationStructureToMemoryKHR.html)

```julia
_copy_acceleration_structure_to_memory_khr(
    device,
    info::Vulkan._CopyAccelerationStructureToMemoryInfoKHR;
    deferred_operation
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
