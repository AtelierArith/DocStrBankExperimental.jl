中間ラッパー VkImportSemaphoreFdInfoKHR。

拡張: VK*KHR*external*semaphore*fd

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportSemaphoreFdInfoKHR.html)

```julia
struct _ImportSemaphoreFdInfoKHR <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkImportSemaphoreFdInfoKHR`
  * `deps::Vector{Any}`
  * `semaphore::Vulkan.Semaphore`
