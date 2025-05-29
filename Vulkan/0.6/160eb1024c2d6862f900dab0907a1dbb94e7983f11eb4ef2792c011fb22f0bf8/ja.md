VkSemaphoreGetFdInfoKHRの高レベルラッパー。

拡張: VK*KHR*external*semaphore*fd

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreGetFdInfoKHR.html)

```julia
struct SemaphoreGetFdInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `semaphore::Vulkan.Semaphore`
  * `handle_type::Vulkan.ExternalSemaphoreHandleTypeFlag`
