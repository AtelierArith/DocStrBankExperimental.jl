拡張: VK*EXT*pipeline_robustness

引数:

  * `storage_buffers::PipelineRobustnessBufferBehaviorEXT`
  * `uniform_buffers::PipelineRobustnessBufferBehaviorEXT`
  * `vertex_inputs::PipelineRobustnessBufferBehaviorEXT`
  * `images::PipelineRobustnessImageBehaviorEXT`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineRobustnessCreateInfoEXT.html)

```julia
PipelineRobustnessCreateInfoEXT(
    storage_buffers::Vulkan.PipelineRobustnessBufferBehaviorEXT,
    uniform_buffers::Vulkan.PipelineRobustnessBufferBehaviorEXT,
    vertex_inputs::Vulkan.PipelineRobustnessBufferBehaviorEXT,
    images::Vulkan.PipelineRobustnessImageBehaviorEXT;
    next
) -> Vulkan.PipelineRobustnessCreateInfoEXT

```
