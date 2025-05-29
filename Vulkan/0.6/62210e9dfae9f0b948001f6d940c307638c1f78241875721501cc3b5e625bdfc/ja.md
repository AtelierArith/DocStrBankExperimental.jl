引数:

  * `device::Device`
  * `fence::Fence` (externsync)
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyFence.html)

```julia
_destroy_fence(device, fence; allocator)

```
