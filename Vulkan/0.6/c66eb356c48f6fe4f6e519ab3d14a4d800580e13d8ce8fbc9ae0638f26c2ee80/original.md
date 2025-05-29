Extension: VK_NV_ray_tracing

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `create_info::AccelerationStructureCreateInfoNV`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateAccelerationStructureNV.html)

```julia
create_acceleration_structure_nv(
    device,
    create_info::Vulkan.AccelerationStructureCreateInfoNV;
    allocator
) -> ResultTypes.Result{Vulkan.AccelerationStructureNV, Vulkan.VulkanError}

```
