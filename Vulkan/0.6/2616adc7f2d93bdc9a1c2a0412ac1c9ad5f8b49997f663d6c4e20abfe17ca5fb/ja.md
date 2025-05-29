VkXlibSurfaceCreateInfoKHRの高レベルラッパー。

拡張: VK*KHR*xlib_surface

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkXlibSurfaceCreateInfoKHR.html)

```julia
struct XlibSurfaceCreateInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `dpy::Ptr{Nothing}`
  * `window::UInt64`
