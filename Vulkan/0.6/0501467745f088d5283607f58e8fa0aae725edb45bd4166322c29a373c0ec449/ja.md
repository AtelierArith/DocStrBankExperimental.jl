VkShaderStatisticsInfoAMDの高レベルラッパー。

拡張: VK*AMD*shader_info

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkShaderStatisticsInfoAMD.html)

```julia
struct ShaderStatisticsInfoAMD <: Vulkan.HighLevelStruct
```

  * `shader_stage_mask::Vulkan.ShaderStageFlag`
  * `resource_usage::Vulkan.ShaderResourceUsageAMD`
  * `num_physical_vgprs::UInt32`
  * `num_physical_sgprs::UInt32`
  * `num_available_vgprs::UInt32`
  * `num_available_sgprs::UInt32`
  * `compute_work_group_size::Tuple{UInt32, UInt32, UInt32}`
