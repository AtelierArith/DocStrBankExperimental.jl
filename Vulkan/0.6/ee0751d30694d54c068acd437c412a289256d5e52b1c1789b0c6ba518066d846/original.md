Extension: VK_KHR_get_surface_capabilities2

Arguments:

  * `surface_capabilities::_SurfaceCapabilitiesKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfaceCapabilities2KHR.html)

```julia
_SurfaceCapabilities2KHR(
    surface_capabilities::Vulkan._SurfaceCapabilitiesKHR;
    next
) -> Vulkan._SurfaceCapabilities2KHR

```
