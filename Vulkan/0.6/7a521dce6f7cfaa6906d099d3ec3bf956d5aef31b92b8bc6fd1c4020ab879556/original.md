Arguments:

  * `logic_op_enable::Bool`
  * `logic_op::LogicOp`
  * `attachments::Vector{_PipelineColorBlendAttachmentState}`
  * `blend_constants::NTuple{4, Float32}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::PipelineColorBlendStateCreateFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineColorBlendStateCreateInfo.html)

```julia
_PipelineColorBlendStateCreateInfo(
    logic_op_enable::Bool,
    logic_op::Vulkan.LogicOp,
    attachments::AbstractArray,
    blend_constants::NTuple{4, Float32};
    next,
    flags
) -> Vulkan._PipelineColorBlendStateCreateInfo

```
