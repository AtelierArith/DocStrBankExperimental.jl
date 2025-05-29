High-level wrapper for VkXlibSurfaceCreateInfoKHR.

Extension: VK_KHR_xlib_surface

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkXlibSurfaceCreateInfoKHR.html)

```julia
struct XlibSurfaceCreateInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `dpy::Ptr{Nothing}`
  * `window::UInt64`
