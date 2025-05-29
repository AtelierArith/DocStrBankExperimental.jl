Extension: VK_KHR_wayland_surface

Arguments:

  * `display::Ptr{wl_display}`
  * `surface::Ptr{wl_surface}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkWaylandSurfaceCreateInfoKHR.html)

```julia
WaylandSurfaceCreateInfoKHR(
    display::Ptr{Nothing},
    surface::Ptr{Nothing};
    next,
    flags
) -> Vulkan.WaylandSurfaceCreateInfoKHR

```
