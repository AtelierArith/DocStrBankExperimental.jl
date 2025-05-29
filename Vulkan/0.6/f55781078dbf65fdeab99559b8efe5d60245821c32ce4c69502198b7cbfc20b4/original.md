Extension: VK_NV_ray_tracing

Arguments:

  * `device::Device`
  * `info::AccelerationStructureMemoryRequirementsInfoNV`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetAccelerationStructureMemoryRequirementsNV.html)

```julia
get_acceleration_structure_memory_requirements_nv(
    device,
    info::Vulkan.AccelerationStructureMemoryRequirementsInfoNV
) -> VulkanCore.LibVulkan.VkMemoryRequirements2

```
