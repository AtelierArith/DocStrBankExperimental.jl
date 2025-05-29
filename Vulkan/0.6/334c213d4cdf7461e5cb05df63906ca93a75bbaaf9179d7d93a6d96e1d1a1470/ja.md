戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `descriptor_update_entries::Vector{_DescriptorUpdateTemplateEntry}`
  * `template_type::DescriptorUpdateTemplateType`
  * `descriptor_set_layout::DescriptorSetLayout`
  * `pipeline_bind_point::PipelineBindPoint`
  * `pipeline_layout::PipelineLayout`
  * `set::UInt32`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDescriptorUpdateTemplate.html)

```julia
_create_descriptor_update_template(
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
) -> ResultTypes.Result{Vulkan.DescriptorUpdateTemplate, Vulkan.VulkanError}

```
