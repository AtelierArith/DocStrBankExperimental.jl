Extension: VK_NV_ray_tracing

Arguments:

  * `device::Device`
  * `compacted_size::UInt64`
  * `info::_AccelerationStructureInfoNV`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateAccelerationStructureNV.html)

```julia
AccelerationStructureNV(
    device,
    compacted_size::Integer,
    info::Vulkan._AccelerationStructureInfoNV;
    allocator,
    next
) -> Vulkan.AccelerationStructureNV

```
