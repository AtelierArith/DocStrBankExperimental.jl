Arguments:

  * `required_subgroup_size::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineShaderStageRequiredSubgroupSizeCreateInfo.html)

```julia
_PipelineShaderStageRequiredSubgroupSizeCreateInfo(
    required_subgroup_size::Integer;
    next
) -> Vulkan._PipelineShaderStageRequiredSubgroupSizeCreateInfo

```
