拡張: VK*NV*device*diagnostic*checkpoints

引数:

  * `stage::PipelineStageFlag`
  * `checkpoint_marker::Ptr{Cvoid}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCheckpointDataNV.html)

```julia
_CheckpointDataNV(
    stage::Vulkan.PipelineStageFlag,
    checkpoint_marker::Ptr{Nothing};
    next
) -> Vulkan._CheckpointDataNV

```
