Extension: VK_NV_device_diagnostic_checkpoints

Arguments:

  * `stage::PipelineStageFlag`
  * `checkpoint_marker::Ptr{Cvoid}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCheckpointDataNV.html)

```julia
CheckpointDataNV(
    stage::Vulkan.PipelineStageFlag,
    checkpoint_marker::Ptr{Nothing};
    next
) -> Vulkan.CheckpointDataNV

```
