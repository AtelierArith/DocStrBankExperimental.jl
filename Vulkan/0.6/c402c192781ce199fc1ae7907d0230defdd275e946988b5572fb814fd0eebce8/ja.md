VkSemaphoreCreateInfoの中間ラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSemaphoreCreateInfo.html)

```julia
struct _SemaphoreCreateInfo <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkSemaphoreCreateInfo`
  * `deps::Vector{Any}`
