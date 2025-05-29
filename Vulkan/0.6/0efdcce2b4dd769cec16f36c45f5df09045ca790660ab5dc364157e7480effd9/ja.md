引数:

  * `device::Device`
  * `query_pool::QueryPool` (externsync)
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyQueryPool.html)

```julia
_destroy_query_pool(device, query_pool; allocator)

```
