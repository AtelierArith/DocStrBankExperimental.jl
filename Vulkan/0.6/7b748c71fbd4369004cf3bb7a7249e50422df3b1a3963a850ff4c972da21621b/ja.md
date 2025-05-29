戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `create_info::DescriptorUpdateTemplateCreateInfo`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDescriptorUpdateTemplate.html)

```julia
create_descriptor_update_template(
    device,
    create_info::Vulkan.DescriptorUpdateTemplateCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.DescriptorUpdateTemplate, Vulkan.VulkanError}

```
