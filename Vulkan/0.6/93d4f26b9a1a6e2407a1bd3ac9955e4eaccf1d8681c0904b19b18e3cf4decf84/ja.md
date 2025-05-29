拡張: VK*KHR*wayland_surface

引数:

  * `display::Ptr{wl_display}`
  * `surface::Ptr{wl_surface}`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkWaylandSurfaceCreateInfoKHR.html)

```julia
WaylandSurfaceCreateInfoKHR(
    display::Ptr{Nothing},
    surface::Ptr{Nothing};
    next,
    flags
) -> Vulkan.WaylandSurfaceCreateInfoKHR

```
