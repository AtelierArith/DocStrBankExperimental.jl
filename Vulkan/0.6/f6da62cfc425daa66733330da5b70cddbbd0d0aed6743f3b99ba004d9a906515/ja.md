戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `create_info::_DescriptorSetLayoutCreateInfo`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDescriptorSetLayout.html)

```julia
_create_descriptor_set_layout(
    device,
    create_info::Vulkan._DescriptorSetLayoutCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.DescriptorSetLayout, Vulkan.VulkanError}

```
