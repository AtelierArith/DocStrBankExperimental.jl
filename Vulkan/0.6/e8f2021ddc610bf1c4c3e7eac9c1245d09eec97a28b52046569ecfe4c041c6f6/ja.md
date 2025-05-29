VkSemaphoreWaitInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreWaitInfo.html)

```julia
struct SemaphoreWaitInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.SemaphoreWaitFlag`
  * `semaphores::Vector{Vulkan.Semaphore}`
  * `values::Vector{UInt64}`
