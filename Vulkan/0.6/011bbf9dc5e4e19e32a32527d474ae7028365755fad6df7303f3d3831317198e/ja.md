拡張: VK*KHR*acceleration_structure

戻りコード:

  * `SUCCESS`
  * `OPERATION_DEFERRED_KHR`
  * `OPERATION_NOT_DEFERRED_KHR`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `info::CopyMemoryToAccelerationStructureInfoKHR`
  * `deferred_operation::DeferredOperationKHR`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCopyMemoryToAccelerationStructureKHR.html)

```julia
copy_memory_to_acceleration_structure_khr(
    device,
    info::Vulkan.CopyMemoryToAccelerationStructureInfoKHR;
    deferred_operation
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
