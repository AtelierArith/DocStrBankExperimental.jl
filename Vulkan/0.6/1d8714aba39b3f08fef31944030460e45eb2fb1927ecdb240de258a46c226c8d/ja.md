引数:

  * `device::Device`
  * `fence::Fence` (externsync)
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyFence.html)

```julia
destroy_fence(device, fence; allocator)

```
