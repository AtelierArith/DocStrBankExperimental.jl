戻りコード:

  * `SUCCESS`
  * `NOT_READY`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`

引数:

  * `device::Device`
  * `query_pool::QueryPool`
  * `first_query::UInt32`
  * `query_count::UInt32`
  * `data_size::UInt`
  * `data::Ptr{Cvoid}` (必ず `data_size` バイトの有効なポインタである必要があります)
  * `stride::UInt64`
  * `flags::QueryResultFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetQueryPoolResults.html)

```julia
_get_query_pool_results(
    device,
    query_pool,
    first_query::Integer,
    query_count::Integer,
    data_size::Integer,
    data::Ptr{Nothing},
    stride::Integer;
    flags
) -> ResultTypes.Result{Vulkan.Result, Vulkan.VulkanError}

```
