Extension: VK_NV_device_diagnostic_checkpoints

Arguments:

  * `stage::PipelineStageFlag`
  * `checkpoint_marker::Ptr{Cvoid}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCheckpointDataNV.html)

```julia
_CheckpointDataNV(
    stage::Vulkan.PipelineStageFlag,
    checkpoint_marker::Ptr{Nothing};
    next
) -> Vulkan._CheckpointDataNV

```
