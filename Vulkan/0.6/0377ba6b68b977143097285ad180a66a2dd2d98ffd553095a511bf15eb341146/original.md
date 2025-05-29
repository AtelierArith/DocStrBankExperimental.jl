Extension: VK_KHR_xcb_surface

Arguments:

  * `connection::Ptr{xcb_connection_t}`
  * `window::xcb_window_t`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkXcbSurfaceCreateInfoKHR.html)

```julia
_XcbSurfaceCreateInfoKHR(
    connection::Ptr{Nothing},
    window::UInt32;
    next,
    flags
) -> Vulkan._XcbSurfaceCreateInfoKHR

```
