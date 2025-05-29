Arguments:

  * `memory_properties::_PhysicalDeviceMemoryProperties`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMemoryProperties2.html)

```julia
_PhysicalDeviceMemoryProperties2(
    memory_properties::Vulkan._PhysicalDeviceMemoryProperties;
    next
) -> Vulkan._PhysicalDeviceMemoryProperties2

```
