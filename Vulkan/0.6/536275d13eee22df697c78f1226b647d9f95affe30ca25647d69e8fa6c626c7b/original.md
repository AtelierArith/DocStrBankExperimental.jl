Arguments:

  * `pipeline_creation_feedback::PipelineCreationFeedback`
  * `pipeline_stage_creation_feedbacks::Vector{PipelineCreationFeedback}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCreationFeedbackCreateInfo.html)

```julia
PipelineCreationFeedbackCreateInfo(
    pipeline_creation_feedback::Vulkan.PipelineCreationFeedback,
    pipeline_stage_creation_feedbacks::AbstractArray;
    next
) -> Vulkan.PipelineCreationFeedbackCreateInfo

```
