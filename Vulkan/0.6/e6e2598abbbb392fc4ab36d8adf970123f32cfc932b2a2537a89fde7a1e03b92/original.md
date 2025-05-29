Intermediate wrapper for VkWriteDescriptorSet.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkWriteDescriptorSet.html)

```julia
struct _WriteDescriptorSet <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkWriteDescriptorSet`
  * `deps::Vector{Any}`
  * `dst_set::Vulkan.DescriptorSet`
