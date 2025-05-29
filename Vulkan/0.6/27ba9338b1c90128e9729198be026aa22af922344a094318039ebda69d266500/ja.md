VkPipelineColorBlendStateCreateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineColorBlendStateCreateInfo.html)

```julia
struct PipelineColorBlendStateCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `flags::Vulkan.PipelineColorBlendStateCreateFlag`
  * `logic_op_enable::Bool`
  * `logic_op::Vulkan.LogicOp`
  * `attachments::Union{Ptr{Nothing}, Vector{Vulkan.PipelineColorBlendAttachmentState}}`
  * `blend_constants::NTuple{4, Float32}`
