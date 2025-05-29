VkSemaphoreSubmitInfoの中間ラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreSubmitInfo.html)

```julia
struct _SemaphoreSubmitInfo <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkSemaphoreSubmitInfo`
  * `deps::Vector{Any}`
  * `semaphore::Vulkan.Semaphore`
