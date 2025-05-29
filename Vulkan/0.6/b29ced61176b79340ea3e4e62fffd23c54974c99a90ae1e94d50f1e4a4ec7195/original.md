High-level wrapper for VkSemaphoreSignalInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreSignalInfo.html)

```julia
struct SemaphoreSignalInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `semaphore::Vulkan.Semaphore`
  * `value::UInt64`
