拡張: VK*KHR*acceleration_structure

戻りコード:

  * `SUCCESS`
  * `OPERATION_DEFERRED_KHR`
  * `OPERATION_NOT_DEFERRED_KHR`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `infos::Vector{AccelerationStructureBuildGeometryInfoKHR}`
  * `build_range_infos::Vector{AccelerationStructureBuildRangeInfoKHR}`
  * `deferred_operation::DeferredOperationKHR`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkBuildAccelerationStructuresKHR.html)

```julia
build_acceleration_structures_khr(
    device,
    infos::AbstractArray,
    build_range_infos::AbstractArray;
    deferred_operation
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
