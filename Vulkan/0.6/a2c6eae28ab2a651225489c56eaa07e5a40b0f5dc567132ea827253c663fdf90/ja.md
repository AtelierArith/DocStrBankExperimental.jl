VkSemaphoreWaitInfoの中間ラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreWaitInfo.html)

```julia
struct _SemaphoreWaitInfo <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkSemaphoreWaitInfo`
  * `deps::Vector{Any}`
