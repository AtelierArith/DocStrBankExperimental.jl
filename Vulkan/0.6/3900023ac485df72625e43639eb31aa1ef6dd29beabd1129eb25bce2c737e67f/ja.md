VkPipelineRobustnessCreateInfoEXTの高レベルラッパー。

拡張: VK*EXT*pipeline_robustness

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineRobustnessCreateInfoEXT.html)

```julia
struct PipelineRobustnessCreateInfoEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `storage_buffers::Vulkan.PipelineRobustnessBufferBehaviorEXT`
  * `uniform_buffers::Vulkan.PipelineRobustnessBufferBehaviorEXT`
  * `vertex_inputs::Vulkan.PipelineRobustnessBufferBehaviorEXT`
  * `images::Vulkan.PipelineRobustnessImageBehaviorEXT`
