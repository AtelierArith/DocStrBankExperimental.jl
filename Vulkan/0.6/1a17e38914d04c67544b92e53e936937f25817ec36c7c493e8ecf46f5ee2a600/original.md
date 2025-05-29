Arguments:

  * `vulkan_memory_model::Bool`
  * `vulkan_memory_model_device_scope::Bool`
  * `vulkan_memory_model_availability_visibility_chains::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceVulkanMemoryModelFeatures.html)

```julia
_PhysicalDeviceVulkanMemoryModelFeatures(
    vulkan_memory_model::Bool,
    vulkan_memory_model_device_scope::Bool,
    vulkan_memory_model_availability_visibility_chains::Bool;
    next
) -> Vulkan._PhysicalDeviceVulkanMemoryModelFeatures

```
