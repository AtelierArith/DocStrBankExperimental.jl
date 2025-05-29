Intermediate wrapper for VkCopyDescriptorSet.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCopyDescriptorSet.html)

```julia
struct _CopyDescriptorSet <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkCopyDescriptorSet`
  * `deps::Vector{Any}`
  * `src_set::Vulkan.DescriptorSet`
  * `dst_set::Vulkan.DescriptorSet`
