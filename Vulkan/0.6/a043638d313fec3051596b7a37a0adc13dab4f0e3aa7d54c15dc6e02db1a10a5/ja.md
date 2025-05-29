拡張: VK*NV*ray_tracing

引数:

  * `acceleration_structure::AccelerationStructureNV`
  * `memory::DeviceMemory`
  * `memory_offset::UInt64`
  * `device_indices::Vector{UInt32}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindAccelerationStructureMemoryInfoNV.html)

```julia
BindAccelerationStructureMemoryInfoNV(
    acceleration_structure::Vulkan.AccelerationStructureNV,
    memory::Vulkan.DeviceMemory,
    memory_offset::Integer,
    device_indices::AbstractArray;
    next
) -> Vulkan.BindAccelerationStructureMemoryInfoNV

```
