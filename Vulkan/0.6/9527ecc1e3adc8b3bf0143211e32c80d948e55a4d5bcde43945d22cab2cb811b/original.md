High-level wrapper for VkCheckpointDataNV.

Extension: VK_NV_device_diagnostic_checkpoints

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCheckpointDataNV.html)

```julia
struct CheckpointDataNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `stage::Vulkan.PipelineStageFlag`
  * `checkpoint_marker::Ptr{Nothing}`
