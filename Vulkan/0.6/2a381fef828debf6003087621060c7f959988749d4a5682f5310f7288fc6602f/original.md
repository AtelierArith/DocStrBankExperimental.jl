Extension: VK_KHR_surface_protected_capabilities

Arguments:

  * `supports_protected::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSurfaceProtectedCapabilitiesKHR.html)

```julia
_SurfaceProtectedCapabilitiesKHR(
    supports_protected::Bool;
    next
) -> Vulkan._SurfaceProtectedCapabilitiesKHR

```
