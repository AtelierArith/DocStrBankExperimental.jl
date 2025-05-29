VkSemaphoreSubmitInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreSubmitInfo.html)

```julia
struct SemaphoreSubmitInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `semaphore::Vulkan.Semaphore`
  * `value::UInt64`
  * `stage_mask::UInt64`
  * `device_index::UInt32`
