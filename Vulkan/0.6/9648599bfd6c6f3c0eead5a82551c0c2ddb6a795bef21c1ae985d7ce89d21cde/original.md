High-level wrapper for VkDisplayPresentInfoKHR.

Extension: VK_KHR_display_swapchain

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPresentInfoKHR.html)

```julia
struct DisplayPresentInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_rect::Vulkan.Rect2D`
  * `dst_rect::Vulkan.Rect2D`
  * `persistent::Bool`
