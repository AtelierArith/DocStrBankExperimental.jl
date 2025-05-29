High-level wrapper for VkPhysicalDevicePipelineRobustnessPropertiesEXT.

Extension: VK_EXT_pipeline_robustness

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDevicePipelineRobustnessPropertiesEXT.html)

```julia
struct PhysicalDevicePipelineRobustnessPropertiesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `default_robustness_storage_buffers::Vulkan.PipelineRobustnessBufferBehaviorEXT`
  * `default_robustness_uniform_buffers::Vulkan.PipelineRobustnessBufferBehaviorEXT`
  * `default_robustness_vertex_inputs::Vulkan.PipelineRobustnessBufferBehaviorEXT`
  * `default_robustness_images::Vulkan.PipelineRobustnessImageBehaviorEXT`
