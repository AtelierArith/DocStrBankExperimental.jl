VkDescriptorUpdateTemplateCreateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorUpdateTemplateCreateInfo.html)

```julia
struct DescriptorUpdateTemplateCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `descriptor_update_entries::Vector{Vulkan.DescriptorUpdateTemplateEntry}`
  * `template_type::Vulkan.DescriptorUpdateTemplateType`
  * `descriptor_set_layout::Vulkan.DescriptorSetLayout`
  * `pipeline_bind_point::Vulkan.PipelineBindPoint`
  * `pipeline_layout::Vulkan.PipelineLayout`
  * `set::UInt32`
