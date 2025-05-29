Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `create_info::DescriptorSetLayoutCreateInfo`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDescriptorSetLayout.html)

```julia
create_descriptor_set_layout(
    device,
    create_info::Vulkan.DescriptorSetLayoutCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.DescriptorSetLayout, Vulkan.VulkanError}

```
