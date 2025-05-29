戻り値のコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`

引数:

  * `device::Device`
  * `query_type::QueryType`
  * `query_count::UInt32`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `pipeline_statistics::QueryPipelineStatisticFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateQueryPool.html)

```julia
_create_query_pool(
    device,
    query_type::Vulkan.QueryType,
    query_count::Integer;
    allocator,
    next,
    flags,
    pipeline_statistics
) -> ResultTypes.Result{Vulkan.QueryPool, Vulkan.VulkanError}

```
