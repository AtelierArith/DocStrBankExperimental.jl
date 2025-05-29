拡張: VK*NV*device*diagnostic*checkpoints

引数:

  * `checkpoint_execution_stage_mask::PipelineStageFlag`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyCheckpointPropertiesNV.html)

```julia
_QueueFamilyCheckpointPropertiesNV(
    checkpoint_execution_stage_mask::Vulkan.PipelineStageFlag;
    next
) -> Vulkan._QueueFamilyCheckpointPropertiesNV

```
