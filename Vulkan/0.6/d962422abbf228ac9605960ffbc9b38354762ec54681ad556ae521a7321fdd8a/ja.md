VkBindBufferMemoryInfoの中間ラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindBufferMemoryInfo.html)

```julia
struct _BindBufferMemoryInfo <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkBindBufferMemoryInfo`
  * `deps::Vector{Any}`
  * `buffer::Vulkan.Buffer`
  * `memory::Vulkan.DeviceMemory`
