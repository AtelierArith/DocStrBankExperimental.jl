Arguments:

  * `device::Device`
  * `fence::Fence` (externsync)
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyFence.html)

```julia
destroy_fence(device, fence; allocator)

```
