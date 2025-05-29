VkIndirectCommandsLayoutCreateInfoNVの高レベルラッパー。

拡張: VK*NV*device*generated*commands

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkIndirectCommandsLayoutCreateInfoNV.html)

```julia
struct IndirectCommandsLayoutCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.IndirectCommandsLayoutUsageFlagNV`
  * `pipeline_bind_point::Vulkan.PipelineBindPoint`
  * `tokens::Vector{Vulkan.IndirectCommandsLayoutTokenNV}`
  * `stream_strides::Vector{UInt32}`
