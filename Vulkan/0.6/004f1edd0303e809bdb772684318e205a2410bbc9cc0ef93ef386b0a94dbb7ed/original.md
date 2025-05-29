Arguments:

  * `device::Device`
  * `query_pool::QueryPool` (externsync)
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkDestroyQueryPool.html)

```julia
destroy_query_pool(device, query_pool; allocator)

```
