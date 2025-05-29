引数:

  * `device::Device`
  * `descriptor_update_entries::Vector{DescriptorUpdateTemplateEntry}`
  * `template_type::DescriptorUpdateTemplateType`
  * `descriptor_set_layout::DescriptorSetLayout`
  * `pipeline_bind_point::PipelineBindPoint`
  * `pipeline_layout::PipelineLayout`
  * `set::UInt32`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDescriptorUpdateTemplate.html)

```julia
DescriptorUpdateTemplate(
    device,
    descriptor_update_entries::AbstractArray,
    template_type::Vulkan.DescriptorUpdateTemplateType,
    descriptor_set_layout,
    pipeline_bind_point::Vulkan.PipelineBindPoint,
    pipeline_layout,
    set::Integer;
    allocator,
    next,
    flags
) -> Vulkan.DescriptorUpdateTemplate

```
