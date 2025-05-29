VkCheckpointDataNVの高レベルラッパー。

拡張: VK*NV*device*diagnostic*checkpoints

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCheckpointDataNV.html)

```julia
struct CheckpointDataNV <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `stage::Vulkan.PipelineStageFlag`
  * `checkpoint_marker::Ptr{Nothing}`
