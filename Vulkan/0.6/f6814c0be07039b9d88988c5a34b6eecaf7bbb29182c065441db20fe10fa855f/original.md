High-level wrapper for VkAccelerationStructureInfoNV.

Extension: VK_NV_ray_tracing

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureInfoNV.html)

```julia
struct AccelerationStructureInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `type::VulkanCore.LibVulkan.VkAccelerationStructureTypeKHR`
  * `flags::Union{Ptr{Nothing}, UInt32}`
  * `instance_count::UInt32`
  * `geometries::Vector{Vulkan.GeometryNV}`
