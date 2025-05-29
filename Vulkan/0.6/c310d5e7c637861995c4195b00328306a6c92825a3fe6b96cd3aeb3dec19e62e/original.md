High-level wrapper for VkXcbSurfaceCreateInfoKHR.

Extension: VK_KHR_xcb_surface

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkXcbSurfaceCreateInfoKHR.html)

```julia
struct XcbSurfaceCreateInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `connection::Ptr{Nothing}`
  * `window::UInt32`
