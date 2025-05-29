Intermediate wrapper for VkAccelerationStructureBuildGeometryInfoKHR.

Extension: VK_KHR_acceleration_structure

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureBuildGeometryInfoKHR.html)

```julia
struct _AccelerationStructureBuildGeometryInfoKHR <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkAccelerationStructureBuildGeometryInfoKHR`
  * `deps::Vector{Any}`
  * `src_acceleration_structure::Union{Ptr{Nothing}, Vulkan.AccelerationStructureKHR}`
  * `dst_acceleration_structure::Union{Ptr{Nothing}, Vulkan.AccelerationStructureKHR}`
