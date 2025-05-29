引数:

  * `src_subpass::UInt32`
  * `dst_subpass::UInt32`
  * `src_stage_mask::PipelineStageFlag`: デフォルトは `0`
  * `dst_stage_mask::PipelineStageFlag`: デフォルトは `0`
  * `src_access_mask::AccessFlag`: デフォルトは `0`
  * `dst_access_mask::AccessFlag`: デフォルトは `0`
  * `dependency_flags::DependencyFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubpassDependency.html)

```julia
_SubpassDependency(
    src_subpass::Integer,
    dst_subpass::Integer;
    src_stage_mask,
    dst_stage_mask,
    src_access_mask,
    dst_access_mask,
    dependency_flags
) -> Vulkan._SubpassDependency

```
