Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_FRAGMENTATION_EXT`

Arguments:

  * `device::Device`
  * `max_sets::UInt32`
  * `pool_sizes::Vector{DescriptorPoolSize}`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::DescriptorPoolCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDescriptorPool.html)

```julia
create_descriptor_pool(
    device,
    max_sets::Integer,
    pool_sizes::AbstractArray;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.DescriptorPool, Vulkan.VulkanError}

```
