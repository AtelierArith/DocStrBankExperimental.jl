Extension: VK_NV_device_diagnostic_checkpoints

Arguments:

  * `checkpoint_execution_stage_mask::PipelineStageFlag`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkQueueFamilyCheckpointPropertiesNV.html)

```julia
QueueFamilyCheckpointPropertiesNV(
    checkpoint_execution_stage_mask::Vulkan.PipelineStageFlag;
    next
) -> Vulkan.QueueFamilyCheckpointPropertiesNV

```
