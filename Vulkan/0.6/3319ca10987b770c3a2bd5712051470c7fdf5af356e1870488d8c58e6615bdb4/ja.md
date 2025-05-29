引数:

  * `device::Device`
  * `query_type::QueryType`
  * `query_count::UInt32`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `pipeline_statistics::QueryPipelineStatisticFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateQueryPool.html)

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
