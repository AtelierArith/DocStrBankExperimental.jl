引数:

  * `vulkan_memory_model::Bool`
  * `vulkan_memory_model_device_scope::Bool`
  * `vulkan_memory_model_availability_visibility_chains::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceVulkanMemoryModelFeatures.html)

```julia
_PhysicalDeviceVulkanMemoryModelFeatures(
    vulkan_memory_model::Bool,
    vulkan_memory_model_device_scope::Bool,
    vulkan_memory_model_availability_visibility_chains::Bool;
    next
) -> Vulkan._PhysicalDeviceVulkanMemoryModelFeatures

```
