Extension: VK_EXT_surface_maintenance1

Arguments:

  * `present_mode::PresentModeKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfacePresentModeEXT.html)

```julia
_SurfacePresentModeEXT(
    present_mode::Vulkan.PresentModeKHR;
    next
) -> Vulkan._SurfacePresentModeEXT

```
