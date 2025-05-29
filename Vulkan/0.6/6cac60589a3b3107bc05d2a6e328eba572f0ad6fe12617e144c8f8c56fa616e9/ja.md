戻り値のコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_FRAGMENTATION_EXT`

引数:

  * `device::Device`
  * `max_sets::UInt32`
  * `pool_sizes::Vector{DescriptorPoolSize}`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::DescriptorPoolCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDescriptorPool.html)

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
