High-level wrapper for VkSemaphoreGetFdInfoKHR.

Extension: VK_KHR_external_semaphore_fd

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreGetFdInfoKHR.html)

```julia
struct SemaphoreGetFdInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `semaphore::Vulkan.Semaphore`
  * `handle_type::Vulkan.ExternalSemaphoreHandleTypeFlag`
