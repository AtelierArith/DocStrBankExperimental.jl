高レベルのラッパー VkComputePipelineCreateInfo。

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkComputePipelineCreateInfo.html)

```julia
struct ComputePipelineCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.PipelineCreateFlag`
  * `stage::Vulkan.PipelineShaderStageCreateInfo`
  * `layout::Vulkan.PipelineLayout`
  * `base_pipeline_handle::Union{Ptr{Nothing}, Vulkan.Pipeline}`
  * `base_pipeline_index::Int32`
