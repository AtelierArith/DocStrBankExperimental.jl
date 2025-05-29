Intermediate wrapper for VkImportSemaphoreFdInfoKHR.

Extension: VK_KHR_external_semaphore_fd

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportSemaphoreFdInfoKHR.html)

```julia
struct _ImportSemaphoreFdInfoKHR <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkImportSemaphoreFdInfoKHR`
  * `deps::Vector{Any}`
  * `semaphore::Vulkan.Semaphore`
