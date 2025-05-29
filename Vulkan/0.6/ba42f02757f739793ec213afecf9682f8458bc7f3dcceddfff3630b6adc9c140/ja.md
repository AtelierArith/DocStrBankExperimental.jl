VkQueryPoolCreateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueryPoolCreateInfo.html)

```julia
struct QueryPoolCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `query_type::Vulkan.QueryType`
  * `query_count::UInt32`
  * `pipeline_statistics::Vulkan.QueryPipelineStatisticFlag`
