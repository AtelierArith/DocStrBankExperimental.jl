Arguments:

  * `device::Device`
  * `query_type::QueryType`
  * `query_count::UInt32`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `pipeline_statistics::QueryPipelineStatisticFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateQueryPool.html)

```julia
QueryPool(
    device,
    query_type::Vulkan.QueryType,
    query_count::Integer;
    allocator,
    next,
    flags,
    pipeline_statistics
) -> Vulkan.QueryPool

```
