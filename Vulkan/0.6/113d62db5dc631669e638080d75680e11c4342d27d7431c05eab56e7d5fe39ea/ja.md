拡張: VK*KHR*get*surface*capabilities2

引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `surface::SurfaceKHR`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceSurfaceInfo2KHR.html)

```julia
_PhysicalDeviceSurfaceInfo2KHR(
;
    next,
    surface
) -> Vulkan._PhysicalDeviceSurfaceInfo2KHR

```
