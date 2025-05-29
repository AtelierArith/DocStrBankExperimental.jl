Extension: VK_NV_ray_tracing

Arguments:

  * `acceleration_structure::AccelerationStructureNV`
  * `memory::DeviceMemory`
  * `memory_offset::UInt64`
  * `device_indices::Vector{UInt32}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindAccelerationStructureMemoryInfoNV.html)

```julia
_BindAccelerationStructureMemoryInfoNV(
    acceleration_structure,
    memory,
    memory_offset::Integer,
    device_indices::AbstractArray;
    next
) -> Vulkan._BindAccelerationStructureMemoryInfoNV

```
