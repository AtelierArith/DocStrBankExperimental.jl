Arguments:

  * `device::Device`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::FenceCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateFence.html)

```julia
Fence(device; allocator, next, flags) -> Vulkan.Fence

```
