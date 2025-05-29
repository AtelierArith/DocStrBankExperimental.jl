Intermediate wrapper for VkMicromapBuildInfoEXT.

Extension: VK_EXT_opacity_micromap

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMicromapBuildInfoEXT.html)

```julia
struct _MicromapBuildInfoEXT <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkMicromapBuildInfoEXT`
  * `deps::Vector{Any}`
  * `dst_micromap::Union{Ptr{Nothing}, Vulkan.MicromapEXT}`
