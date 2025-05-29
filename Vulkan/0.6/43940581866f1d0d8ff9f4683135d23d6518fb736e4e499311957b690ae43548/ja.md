拡張: VK*EXT*pipeline_robustness

引数:

  * `default_robustness_storage_buffers::PipelineRobustnessBufferBehaviorEXT`
  * `default_robustness_uniform_buffers::PipelineRobustnessBufferBehaviorEXT`
  * `default_robustness_vertex_inputs::PipelineRobustnessBufferBehaviorEXT`
  * `default_robustness_images::PipelineRobustnessImageBehaviorEXT`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePipelineRobustnessPropertiesEXT.html)

```julia
PhysicalDevicePipelineRobustnessPropertiesEXT(
    default_robustness_storage_buffers::Vulkan.PipelineRobustnessBufferBehaviorEXT,
    default_robustness_uniform_buffers::Vulkan.PipelineRobustnessBufferBehaviorEXT,
    default_robustness_vertex_inputs::Vulkan.PipelineRobustnessBufferBehaviorEXT,
    default_robustness_images::Vulkan.PipelineRobustnessImageBehaviorEXT;
    next
) -> Vulkan.PhysicalDevicePipelineRobustnessPropertiesEXT

```
