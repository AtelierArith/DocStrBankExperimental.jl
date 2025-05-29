拡張: VK*EXT*surface_maintenance1

引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `present_modes::Vector{PresentModeKHR}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfacePresentModeCompatibilityEXT.html)

```julia
_SurfacePresentModeCompatibilityEXT(
;
    next,
    present_modes
) -> Vulkan._SurfacePresentModeCompatibilityEXT

```
