Intermediate wrapper for VkAccelerationStructureCaptureDescriptorDataInfoEXT.

Extension: VK_EXT_descriptor_buffer

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAccelerationStructureCaptureDescriptorDataInfoEXT.html)

```julia
struct _AccelerationStructureCaptureDescriptorDataInfoEXT <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkAccelerationStructureCaptureDescriptorDataInfoEXT`
  * `deps::Vector{Any}`
  * `acceleration_structure::Union{Ptr{Nothing}, Vulkan.AccelerationStructureKHR}`
  * `acceleration_structure_nv::Union{Ptr{Nothing}, Vulkan.AccelerationStructureNV}`
