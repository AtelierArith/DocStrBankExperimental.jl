Return codes:

  * `SUCCESS`
  * `NOT_READY`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_DEVICE_LOST`

Arguments:

  * `device::Device`
  * `query_pool::QueryPool`
  * `first_query::UInt32`
  * `query_count::UInt32`
  * `data_size::UInt`
  * `data::Ptr{Cvoid}` (must be a valid pointer with `data_size` bytes)
  * `stride::UInt64`
  * `flags::QueryResultFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkGetQueryPoolResults.html)

```julia
get_query_pool_results(
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
