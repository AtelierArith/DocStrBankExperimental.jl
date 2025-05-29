Extension: VK_EXT_surface_maintenance1

Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `present_modes::Vector{PresentModeKHR}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfacePresentModeCompatibilityEXT.html)

```julia
_SurfacePresentModeCompatibilityEXT(
;
    next,
    present_modes
) -> Vulkan._SurfacePresentModeCompatibilityEXT

```
