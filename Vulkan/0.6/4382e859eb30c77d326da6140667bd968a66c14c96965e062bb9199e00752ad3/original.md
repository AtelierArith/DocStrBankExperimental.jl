Extension: VK_NV_ray_tracing

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `acceleration_structure::AccelerationStructureNV`
  * `data_size::UInt`
  * `data::Ptr{Cvoid}` (must be a valid pointer with `data_size` bytes)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetAccelerationStructureHandleNV.html)

```julia
_get_acceleration_structure_handle_nv(
    device,
    acceleration_structure,
    data_size::Integer,
    data::Ptr{Nothing}
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
