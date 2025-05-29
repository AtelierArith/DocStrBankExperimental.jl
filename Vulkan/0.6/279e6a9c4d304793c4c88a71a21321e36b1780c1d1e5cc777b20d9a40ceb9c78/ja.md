拡張: VK*KHR*xlib_surface

引数:

  * `dpy::Ptr{Display}`
  * `window::Window`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkXlibSurfaceCreateInfoKHR.html)

```julia
_XlibSurfaceCreateInfoKHR(
    dpy::Ptr{Nothing},
    window::UInt64;
    next,
    flags
) -> Vulkan._XlibSurfaceCreateInfoKHR

```
