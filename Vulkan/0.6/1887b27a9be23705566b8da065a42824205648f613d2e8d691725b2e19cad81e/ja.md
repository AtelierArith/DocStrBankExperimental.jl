VkPipelineCacheCreateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCacheCreateInfo.html)

```julia
struct PipelineCacheCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.PipelineCacheCreateFlag`
  * `initial_data_size::Union{Ptr{Nothing}, UInt64}`
  * `initial_data::Ptr{Nothing}`
