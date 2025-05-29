拡張: VK*KHR*get*surface*capabilities2

引数:

  * `surface_capabilities::_SurfaceCapabilitiesKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfaceCapabilities2KHR.html)

```julia
_SurfaceCapabilities2KHR(
    surface_capabilities::Vulkan._SurfaceCapabilitiesKHR;
    next
) -> Vulkan._SurfaceCapabilities2KHR

```
