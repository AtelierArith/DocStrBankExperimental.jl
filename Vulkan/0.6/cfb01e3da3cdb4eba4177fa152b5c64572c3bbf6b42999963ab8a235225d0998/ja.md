VkQueueFamilyCheckpointPropertiesNVの高レベルラッパー。

拡張: VK*NV*device*diagnostic*checkpoints

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyCheckpointPropertiesNV.html)

```julia
struct QueueFamilyCheckpointPropertiesNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `checkpoint_execution_stage_mask::Vulkan.PipelineStageFlag`
