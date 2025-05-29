Intermediate wrapper for VkDescriptorUpdateTemplateCreateInfo.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorUpdateTemplateCreateInfo.html)

```julia
struct _DescriptorUpdateTemplateCreateInfo <: Vulkan.VulkanStruct{true}
```

  * `vks::VulkanCore.LibVulkan.VkDescriptorUpdateTemplateCreateInfo`
  * `deps::Vector{Any}`
  * `descriptor_set_layout::Vulkan.DescriptorSetLayout`
  * `pipeline_layout::Vulkan.PipelineLayout`
