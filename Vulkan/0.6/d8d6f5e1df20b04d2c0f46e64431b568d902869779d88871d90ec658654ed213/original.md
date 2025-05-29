Arguments:

  * `device::Device`
  * `queue_family_index::UInt32`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::CommandPoolCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCommandPool.html)

```julia
CommandPool(
    device,
    queue_family_index::Integer;
    allocator,
    next,
    flags
) -> Vulkan.CommandPool

```
