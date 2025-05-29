VkBufferMemoryRequirementsInfo2の中間ラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferMemoryRequirementsInfo2.html)

```julia
struct _BufferMemoryRequirementsInfo2 <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkBufferMemoryRequirementsInfo2`
  * `deps::Vector{Any}`
  * `buffer::Vulkan.Buffer`
