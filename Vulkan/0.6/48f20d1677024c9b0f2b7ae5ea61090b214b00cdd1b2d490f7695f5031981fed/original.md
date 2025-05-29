Intermediate wrapper for VkCopyAccelerationStructureInfoKHR.

Extension: VK_KHR_acceleration_structure

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyAccelerationStructureInfoKHR.html)

```julia
struct _CopyAccelerationStructureInfoKHR <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkCopyAccelerationStructureInfoKHR`
  * `deps::Vector{Any}`
  * `src::Vulkan.AccelerationStructureKHR`
  * `dst::Vulkan.AccelerationStructureKHR`
