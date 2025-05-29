拡張: VK*KHR*get*surface*capabilities2

引数:

  * `surface_format::SurfaceFormatKHR`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfaceFormat2KHR.html)

```julia
SurfaceFormat2KHR(
    surface_format::Vulkan.SurfaceFormatKHR;
    next
) -> Vulkan.SurfaceFormat2KHR

```
