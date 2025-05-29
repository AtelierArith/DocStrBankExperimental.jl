Arguments:

  * `src_subpass::UInt32`
  * `dst_subpass::UInt32`
  * `src_stage_mask::PipelineStageFlag`: defaults to `0`
  * `dst_stage_mask::PipelineStageFlag`: defaults to `0`
  * `src_access_mask::AccessFlag`: defaults to `0`
  * `dst_access_mask::AccessFlag`: defaults to `0`
  * `dependency_flags::DependencyFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubpassDependency.html)

```julia
SubpassDependency(
    src_subpass::Integer,
    dst_subpass::Integer;
    src_stage_mask,
    dst_stage_mask,
    src_access_mask,
    dst_access_mask,
    dependency_flags
) -> Vulkan.SubpassDependency

```
