Intermediate wrapper for VkBindAccelerationStructureMemoryInfoNV.

Extension: VK_NV_ray_tracing

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindAccelerationStructureMemoryInfoNV.html)

```julia
struct _BindAccelerationStructureMemoryInfoNV <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkBindAccelerationStructureMemoryInfoNV`
  * `deps::Vector{Any}`
  * `acceleration_structure::Vulkan.AccelerationStructureNV`
  * `memory::Vulkan.DeviceMemory`
