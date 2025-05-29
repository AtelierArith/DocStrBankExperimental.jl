Intermediate wrapper for VkSemaphoreSignalInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreSignalInfo.html)

```julia
struct _SemaphoreSignalInfo <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkSemaphoreSignalInfo`
  * `deps::Vector{Any}`
  * `semaphore::Vulkan.Semaphore`
