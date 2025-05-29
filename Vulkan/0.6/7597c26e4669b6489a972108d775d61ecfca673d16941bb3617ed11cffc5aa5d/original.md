Intermediate wrapper for VkCopyMicromapInfoEXT.

Extension: VK_EXT_opacity_micromap

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyMicromapInfoEXT.html)

```julia
struct _CopyMicromapInfoEXT <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkCopyMicromapInfoEXT`
  * `deps::Vector{Any}`
  * `src::Vulkan.MicromapEXT`
  * `dst::Vulkan.MicromapEXT`
