Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_FRAGMENTATION_EXT`

Arguments:

  * `device::Device`
  * `create_info::_DescriptorPoolCreateInfo`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDescriptorPool.html)

```julia
_create_descriptor_pool(
    device,
    create_info::Vulkan._DescriptorPoolCreateInfo;
    allocator
) -> ResultTypes.Result{Vulkan.DescriptorPool, Vulkan.VulkanError}

```
