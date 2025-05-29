VkCopyBufferInfo2の中間ラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyBufferInfo2.html)

```julia
struct _CopyBufferInfo2 <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkCopyBufferInfo2`
  * `deps::Vector{Any}`
  * `src_buffer::Vulkan.Buffer`
  * `dst_buffer::Vulkan.Buffer`
