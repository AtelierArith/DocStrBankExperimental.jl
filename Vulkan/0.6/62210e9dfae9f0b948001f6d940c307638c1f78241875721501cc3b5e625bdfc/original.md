Arguments:

  * `device::Device`
  * `fence::Fence` (externsync)
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyFence.html)

```julia
_destroy_fence(device, fence; allocator)

```
