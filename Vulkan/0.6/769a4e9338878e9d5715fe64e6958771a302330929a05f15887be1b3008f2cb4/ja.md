引数:

  * `query_type::QueryType`
  * `query_count::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`
  * `pipeline_statistics::QueryPipelineStatisticFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueryPoolCreateInfo.html)

```julia
_QueryPoolCreateInfo(
    query_type::Vulkan.QueryType,
    query_count::Integer;
    next,
    flags,
    pipeline_statistics
) -> Vulkan._QueryPoolCreateInfo

```
