引数:

  * `features::_PhysicalDeviceFeatures`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFeatures2.html)

```julia
_PhysicalDeviceFeatures2(
    features::Vulkan._PhysicalDeviceFeatures;
    next
) -> Vulkan._PhysicalDeviceFeatures2

```
