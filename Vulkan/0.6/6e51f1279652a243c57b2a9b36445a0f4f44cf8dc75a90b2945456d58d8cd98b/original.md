Extension: VK_EXT_memory_priority

Arguments:

  * `memory_priority::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMemoryPriorityFeaturesEXT.html)

```julia
_PhysicalDeviceMemoryPriorityFeaturesEXT(
    memory_priority::Bool;
    next
) -> Vulkan._PhysicalDeviceMemoryPriorityFeaturesEXT

```
