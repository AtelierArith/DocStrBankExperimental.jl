Extension: VK_EXT_pipeline_robustness

Arguments:

  * `storage_buffers::PipelineRobustnessBufferBehaviorEXT`
  * `uniform_buffers::PipelineRobustnessBufferBehaviorEXT`
  * `vertex_inputs::PipelineRobustnessBufferBehaviorEXT`
  * `images::PipelineRobustnessImageBehaviorEXT`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineRobustnessCreateInfoEXT.html)

```julia
_PipelineRobustnessCreateInfoEXT(
    storage_buffers::Vulkan.PipelineRobustnessBufferBehaviorEXT,
    uniform_buffers::Vulkan.PipelineRobustnessBufferBehaviorEXT,
    vertex_inputs::Vulkan.PipelineRobustnessBufferBehaviorEXT,
    images::Vulkan.PipelineRobustnessImageBehaviorEXT;
    next
) -> Vulkan._PipelineRobustnessCreateInfoEXT

```
