Extension: VK_NV_ray_tracing

Arguments:

  * `device::Device`
  * `acceleration_structure::AccelerationStructureNV` (externsync)
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyAccelerationStructureNV.html)

```julia
destroy_acceleration_structure_nv(
    device,
    acceleration_structure;
    allocator
)

```
