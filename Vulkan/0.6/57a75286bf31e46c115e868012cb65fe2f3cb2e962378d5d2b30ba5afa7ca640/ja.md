VkVideoSessionMemoryRequirementsKHRの高レベルラッパー。

拡張: VK*KHR*video_queue

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoSessionMemoryRequirementsKHR.html)

```julia
struct VideoSessionMemoryRequirementsKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `memory_bind_index::UInt32`
  * `memory_requirements::Vulkan.MemoryRequirements`
