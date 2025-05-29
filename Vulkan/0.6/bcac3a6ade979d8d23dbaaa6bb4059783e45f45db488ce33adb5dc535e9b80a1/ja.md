VkVideoProfileListInfoKHRの高レベルラッパー。

拡張: VK*KHR*video_queue

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoProfileListInfoKHR.html)

```julia
struct VideoProfileListInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `profiles::Vector{Vulkan.VideoProfileInfoKHR}`
