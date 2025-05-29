Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

Arguments:

  * `device::Device`
  * `bindings::Vector{DescriptorSetLayoutBinding}`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::DescriptorSetLayoutCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDescriptorSetLayout.html)

```julia
create_descriptor_set_layout(
    device,
    bindings::AbstractArray;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.DescriptorSetLayout, Vulkan.VulkanError}

```
