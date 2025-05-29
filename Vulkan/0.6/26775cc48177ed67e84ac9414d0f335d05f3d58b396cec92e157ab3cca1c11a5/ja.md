引数:

  * `device::Device`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::FenceCreateFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateFence.html)

```julia
Fence(device; allocator, next, flags) -> Vulkan.Fence

```
