VkSemaphoreTypeCreateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreTypeCreateInfo.html)

```julia
struct SemaphoreTypeCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `semaphore_type::Vulkan.SemaphoreType`
  * `initial_value::UInt64`
