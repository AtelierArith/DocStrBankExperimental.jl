Extension: VK_KHR_acceleration_structure

Arguments:

  * `device::Device`
  * `acceleration_structure::AccelerationStructureKHR` (externsync)
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyAccelerationStructureKHR.html)

```julia
_destroy_acceleration_structure_khr(
    device,
    acceleration_structure;
    allocator
)

```
