拡張: VK*KHR*xcb_surface

引数:

  * `connection::Ptr{xcb_connection_t}`
  * `window::xcb_window_t`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkXcbSurfaceCreateInfoKHR.html)

```julia
XcbSurfaceCreateInfoKHR(
    connection::Ptr{Nothing},
    window::UInt32;
    next,
    flags
) -> Vulkan.XcbSurfaceCreateInfoKHR

```
