Extension: VK_KHR_xlib_surface

Arguments:

  * `dpy::Ptr{Display}`
  * `window::Window`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkXlibSurfaceCreateInfoKHR.html)

```julia
_XlibSurfaceCreateInfoKHR(
    dpy::Ptr{Nothing},
    window::UInt64;
    next,
    flags
) -> Vulkan._XlibSurfaceCreateInfoKHR

```
