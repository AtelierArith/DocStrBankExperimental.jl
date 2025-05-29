引数:

  * `device::Device`
  * `max_sets::UInt32`
  * `pool_sizes::Vector{_DescriptorPoolSize}`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::DescriptorPoolCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateDescriptorPool.html)

```julia
DescriptorPool(
    device,
    max_sets::Integer,
    pool_sizes::AbstractArray{Vulkan._DescriptorPoolSize};
    allocator,
    next,
    flags
) -> Vulkan.DescriptorPool

```
