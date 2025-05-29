High-level wrapper for VkImportSemaphoreFdInfoKHR.

Extension: VK_KHR_external_semaphore_fd

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportSemaphoreFdInfoKHR.html)

```julia
struct ImportSemaphoreFdInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `semaphore::Vulkan.Semaphore`
  * `flags::Vulkan.SemaphoreImportFlag`
  * `handle_type::Vulkan.ExternalSemaphoreHandleTypeFlag`
  * `fd::Int64`
