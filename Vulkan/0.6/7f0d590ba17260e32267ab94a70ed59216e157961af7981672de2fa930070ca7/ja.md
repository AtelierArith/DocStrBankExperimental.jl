拡張: VK*NV*device*diagnostic*checkpoints

引数:

  * `checkpoint_execution_stage_mask::PipelineStageFlag`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyCheckpointPropertiesNV.html)

```julia
QueueFamilyCheckpointPropertiesNV(
    checkpoint_execution_stage_mask::Vulkan.PipelineStageFlag;
    next
) -> Vulkan.QueueFamilyCheckpointPropertiesNV

```
