High-level wrapper for VkBindAccelerationStructureMemoryInfoNV.

Extension: VK_NV_ray_tracing

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindAccelerationStructureMemoryInfoNV.html)

```julia
struct BindAccelerationStructureMemoryInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `acceleration_structure::Vulkan.AccelerationStructureNV`
  * `memory::Vulkan.DeviceMemory`
  * `memory_offset::UInt64`
  * `device_indices::Vector{UInt32}`
