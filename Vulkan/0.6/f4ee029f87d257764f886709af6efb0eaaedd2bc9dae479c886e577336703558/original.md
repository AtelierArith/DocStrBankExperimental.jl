Intermediate wrapper for VkBindImageMemoryInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindImageMemoryInfo.html)

```julia
struct _BindImageMemoryInfo <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkBindImageMemoryInfo`
  * `deps::Vector{Any}`
  * `image::Vulkan.Image`
  * `memory::Vulkan.DeviceMemory`
