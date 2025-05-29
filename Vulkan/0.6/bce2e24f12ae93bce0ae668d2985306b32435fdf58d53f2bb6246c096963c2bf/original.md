Extension: VK_EXT_pipeline_robustness

Arguments:

  * `default_robustness_storage_buffers::PipelineRobustnessBufferBehaviorEXT`
  * `default_robustness_uniform_buffers::PipelineRobustnessBufferBehaviorEXT`
  * `default_robustness_vertex_inputs::PipelineRobustnessBufferBehaviorEXT`
  * `default_robustness_images::PipelineRobustnessImageBehaviorEXT`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePipelineRobustnessPropertiesEXT.html)

```julia
_PhysicalDevicePipelineRobustnessPropertiesEXT(
    default_robustness_storage_buffers::Vulkan.PipelineRobustnessBufferBehaviorEXT,
    default_robustness_uniform_buffers::Vulkan.PipelineRobustnessBufferBehaviorEXT,
    default_robustness_vertex_inputs::Vulkan.PipelineRobustnessBufferBehaviorEXT,
    default_robustness_images::Vulkan.PipelineRobustnessImageBehaviorEXT;
    next
) -> Vulkan._PhysicalDevicePipelineRobustnessPropertiesEXT

```
