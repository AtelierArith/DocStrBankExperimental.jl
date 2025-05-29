拡張: VK*AMD*shader_info

引数:

  * `shader_stage_mask::ShaderStageFlag`
  * `resource_usage::_ShaderResourceUsageAMD`
  * `num_physical_vgprs::UInt32`
  * `num_physical_sgprs::UInt32`
  * `num_available_vgprs::UInt32`
  * `num_available_sgprs::UInt32`
  * `compute_work_group_size::NTuple{3, UInt32}`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkShaderStatisticsInfoAMD.html)

```julia
_ShaderStatisticsInfoAMD(
    shader_stage_mask::Vulkan.ShaderStageFlag,
    resource_usage::Vulkan._ShaderResourceUsageAMD,
    num_physical_vgprs::Integer,
    num_physical_sgprs::Integer,
    num_available_vgprs::Integer,
    num_available_sgprs::Integer,
    compute_work_group_size::Tuple{UInt32, UInt32, UInt32}
) -> Vulkan._ShaderStatisticsInfoAMD

```
