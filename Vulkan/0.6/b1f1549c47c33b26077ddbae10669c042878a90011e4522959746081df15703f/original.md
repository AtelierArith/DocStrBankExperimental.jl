Extension: VK_KHR_acceleration_structure

Return codes:

  * `SUCCESS`
  * `OPERATION_DEFERRED_KHR`
  * `OPERATION_NOT_DEFERRED_KHR`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `infos::Vector{_AccelerationStructureBuildGeometryInfoKHR}`
  * `build_range_infos::Vector{_AccelerationStructureBuildRangeInfoKHR}`
  * `deferred_operation::DeferredOperationKHR`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkBuildAccelerationStructuresKHR.html)

```julia
_build_acceleration_structures_khr(
    device,
    infos::AbstractArray,
    build_range_infos::AbstractArray;
    deferred_operation
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
