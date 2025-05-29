VkDisplayPresentInfoKHRの高レベルラッパー。

拡張: VK*KHR*display_swapchain

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPresentInfoKHR.html)

```julia
struct DisplayPresentInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_rect::Vulkan.Rect2D`
  * `dst_rect::Vulkan.Rect2D`
  * `persistent::Bool`
