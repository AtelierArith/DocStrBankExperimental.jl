VkPipelineMultisampleStateCreateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineMultisampleStateCreateInfo.html)

```julia
struct PipelineMultisampleStateCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::UInt32`
  * `rasterization_samples::Vulkan.SampleCountFlag`
  * `sample_shading_enable::Bool`
  * `min_sample_shading::Float32`
  * `sample_mask::Union{Ptr{Nothing}, Vector{UInt32}}`
  * `alpha_to_coverage_enable::Bool`
  * `alpha_to_one_enable::Bool`
