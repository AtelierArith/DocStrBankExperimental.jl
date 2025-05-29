引数:

  * `properties::_PhysicalDeviceProperties`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceProperties2.html)

```julia
_PhysicalDeviceProperties2(
    properties::Vulkan._PhysicalDeviceProperties;
    next
) -> Vulkan._PhysicalDeviceProperties2

```
