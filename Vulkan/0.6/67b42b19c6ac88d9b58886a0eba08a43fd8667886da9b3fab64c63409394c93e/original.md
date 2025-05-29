Extension: VK_NV_ray_tracing

Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`

Arguments:

  * `device::Device`
  * `compacted_size::UInt64`
  * `info::AccelerationStructureInfoNV`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateAccelerationStructureNV.html)

```julia
create_acceleration_structure_nv(
    device,
    compacted_size::Integer,
    info::Vulkan.AccelerationStructureInfoNV;
    allocator,
    next
) -> ResultTypes.Result{Vulkan.AccelerationStructureNV, Vulkan.VulkanError}

```
