Arguments:

  * `pipeline_creation_feedback::_PipelineCreationFeedback`
  * `pipeline_stage_creation_feedbacks::Vector{_PipelineCreationFeedback}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCreationFeedbackCreateInfo.html)

```julia
_PipelineCreationFeedbackCreateInfo(
    pipeline_creation_feedback::Vulkan._PipelineCreationFeedback,
    pipeline_stage_creation_feedbacks::AbstractArray;
    next
) -> Vulkan._PipelineCreationFeedbackCreateInfo

```
