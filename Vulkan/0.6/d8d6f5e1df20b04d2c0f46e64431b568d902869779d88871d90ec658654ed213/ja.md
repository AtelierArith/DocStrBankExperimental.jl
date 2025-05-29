引数:

  * `device::Device`
  * `queue_family_index::UInt32`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::CommandPoolCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateCommandPool.html)

```julia
CommandPool(
    device,
    queue_family_index::Integer;
    allocator,
    next,
    flags
) -> Vulkan.CommandPool

```
