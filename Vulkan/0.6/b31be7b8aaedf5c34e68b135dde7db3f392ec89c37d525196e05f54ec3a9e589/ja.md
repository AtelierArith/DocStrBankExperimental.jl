VkRayTracingPipelineCreateInfoNVの高レベルラッパー。

拡張: VK*NV*ray_tracing

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRayTracingPipelineCreateInfoNV.html)

```julia
struct RayTracingPipelineCreateInfoNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.PipelineCreateFlag`
  * `stages::Vector{Vulkan.PipelineShaderStageCreateInfo}`
  * `groups::Vector{Vulkan.RayTracingShaderGroupCreateInfoNV}`
  * `max_recursion_depth::UInt32`
  * `layout::Vulkan.PipelineLayout`
  * `base_pipeline_handle::Union{Ptr{Nothing}, Vulkan.Pipeline}`
  * `base_pipeline_index::Int32`
