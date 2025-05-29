拡張: VK*EXT*surface_maintenance1

引数:

  * `present_mode::PresentModeKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfacePresentModeEXT.html)

```julia
_SurfacePresentModeEXT(
    present_mode::Vulkan.PresentModeKHR;
    next
) -> Vulkan._SurfacePresentModeEXT

```
