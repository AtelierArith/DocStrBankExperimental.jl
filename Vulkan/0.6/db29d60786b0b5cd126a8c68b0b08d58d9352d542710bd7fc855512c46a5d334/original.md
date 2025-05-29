Extension: VK_KHR_get_surface_capabilities2

Arguments:

  * `surface_format::_SurfaceFormatKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfaceFormat2KHR.html)

```julia
_SurfaceFormat2KHR(
    surface_format::Vulkan._SurfaceFormatKHR;
    next
) -> Vulkan._SurfaceFormat2KHR

```
