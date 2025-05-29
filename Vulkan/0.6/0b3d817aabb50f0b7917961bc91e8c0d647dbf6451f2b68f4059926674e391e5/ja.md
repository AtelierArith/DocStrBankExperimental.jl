引数:

  * `descriptor_update_entries::Vector{DescriptorUpdateTemplateEntry}`
  * `template_type::DescriptorUpdateTemplateType`
  * `descriptor_set_layout::DescriptorSetLayout`
  * `pipeline_bind_point::PipelineBindPoint`
  * `pipeline_layout::PipelineLayout`
  * `set::UInt32`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDescriptorUpdateTemplateCreateInfo.html)

```julia
DescriptorUpdateTemplateCreateInfo(
    descriptor_update_entries::AbstractArray,
    template_type::Vulkan.DescriptorUpdateTemplateType,
    descriptor_set_layout::Vulkan.DescriptorSetLayout,
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    pipeline_layout::Vulkan.PipelineLayout,
    set::Integer;
    next,
    flags
) -> Vulkan.DescriptorUpdateTemplateCreateInfo

```
