Intermediate wrapper for VkBufferMemoryBarrier.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferMemoryBarrier.html)

```julia
struct _BufferMemoryBarrier <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkBufferMemoryBarrier`
  * `deps::Vector{Any}`
  * `buffer::Vulkan.Buffer`
