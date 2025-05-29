High-level wrapper for VkIndirectCommandsLayoutCreateInfoNV.

Extension: VK_NV_device_generated_commands

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkIndirectCommandsLayoutCreateInfoNV.html)

```julia
struct IndirectCommandsLayoutCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.IndirectCommandsLayoutUsageFlagNV`
  * `pipeline_bind_point::Vulkan.PipelineBindPoint`
  * `tokens::Vector{Vulkan.IndirectCommandsLayoutTokenNV}`
  * `stream_strides::Vector{UInt32}`
