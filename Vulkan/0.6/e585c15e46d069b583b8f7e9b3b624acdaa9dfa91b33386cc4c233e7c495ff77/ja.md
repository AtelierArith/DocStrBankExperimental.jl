VkBufferMemoryBarrier2の中間ラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferMemoryBarrier2.html)

```julia
struct _BufferMemoryBarrier2 <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkBufferMemoryBarrier2`
  * `deps::Vector{Any}`
  * `buffer::Vulkan.Buffer`
