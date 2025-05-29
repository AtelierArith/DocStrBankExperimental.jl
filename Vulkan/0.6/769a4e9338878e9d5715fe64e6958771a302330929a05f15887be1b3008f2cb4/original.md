Arguments:

  * `query_type::QueryType`
  * `query_count::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`
  * `pipeline_statistics::QueryPipelineStatisticFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueryPoolCreateInfo.html)

```julia
_QueryPoolCreateInfo(
    query_type::Vulkan.QueryType,
    query_count::Integer;
    next,
    flags,
    pipeline_statistics
) -> Vulkan._QueryPoolCreateInfo

```
