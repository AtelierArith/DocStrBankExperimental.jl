VkDisplayPlaneInfo2KHRの高レベルラッパー。

拡張: VK*KHR*get*display*properties2

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPlaneInfo2KHR.html)

```julia
struct DisplayPlaneInfo2KHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `mode::Vulkan.DisplayModeKHR`
  * `plane_index::UInt32`
