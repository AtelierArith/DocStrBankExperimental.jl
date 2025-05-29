拡張: VK*KHR*get*surface*capabilities2

引数:

  * `surface_format::_SurfaceFormatKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfaceFormat2KHR.html)

```julia
_SurfaceFormat2KHR(
    surface_format::Vulkan._SurfaceFormatKHR;
    next
) -> Vulkan._SurfaceFormat2KHR

```
