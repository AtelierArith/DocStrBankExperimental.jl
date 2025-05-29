引数:

  * `memory_properties::_PhysicalDeviceMemoryProperties`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceMemoryProperties2.html)

```julia
_PhysicalDeviceMemoryProperties2(
    memory_properties::Vulkan._PhysicalDeviceMemoryProperties;
    next
) -> Vulkan._PhysicalDeviceMemoryProperties2

```
