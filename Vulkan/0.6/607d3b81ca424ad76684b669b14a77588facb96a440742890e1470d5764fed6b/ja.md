引数:

  * `device::Device`
  * `descriptor_pool::DescriptorPool` (externsync)
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyDescriptorPool.html)

```julia
_destroy_descriptor_pool(device, descriptor_pool; allocator)

```
