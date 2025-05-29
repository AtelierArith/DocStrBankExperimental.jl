VkPipelineCreationFeedbackCreateInfoの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineCreationFeedbackCreateInfo.html)

```julia
struct PipelineCreationFeedbackCreateInfo <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `pipeline_creation_feedback::Vulkan.PipelineCreationFeedback`
  * `pipeline_stage_creation_feedbacks::Vector{Vulkan.PipelineCreationFeedback}`
