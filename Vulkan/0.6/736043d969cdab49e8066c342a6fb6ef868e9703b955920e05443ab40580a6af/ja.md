VkImportSemaphoreFdInfoKHRの高レベルラッパー。

拡張: VK*KHR*external*semaphore*fd

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportSemaphoreFdInfoKHR.html)

```julia
struct ImportSemaphoreFdInfoKHR <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `semaphore::Vulkan.Semaphore`
  * `flags::Vulkan.SemaphoreImportFlag`
  * `handle_type::Vulkan.ExternalSemaphoreHandleTypeFlag`
  * `fd::Int64`
