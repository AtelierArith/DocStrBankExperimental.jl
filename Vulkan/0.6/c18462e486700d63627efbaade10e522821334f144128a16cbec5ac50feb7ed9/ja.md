VkWaylandSurfaceCreateInfoKHRの高レベルラッパー。

拡張: VK*KHR*wayland_surface

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkWaylandSurfaceCreateInfoKHR.html)

```julia
struct WaylandSurfaceCreateInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `display::Ptr{Nothing}`
  * `surface::Ptr{Nothing}`
