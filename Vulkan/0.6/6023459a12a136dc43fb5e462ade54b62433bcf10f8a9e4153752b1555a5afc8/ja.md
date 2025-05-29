VkExternalSemaphorePropertiesの中間ラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExternalSemaphoreProperties.html)

```julia
struct _ExternalSemaphoreProperties <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkExternalSemaphoreProperties`
  * `deps::Vector{Any}`
