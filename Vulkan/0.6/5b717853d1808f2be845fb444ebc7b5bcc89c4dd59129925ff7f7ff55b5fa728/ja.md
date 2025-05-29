VkShaderResourceUsageAMDの高レベルラッパー。

拡張: VK*AMD*shader_info

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkShaderResourceUsageAMD.html)

```julia
struct ShaderResourceUsageAMD <: Vulkan.HighLevelStruct
```

  * `num_used_vgprs::UInt32`
  * `num_used_sgprs::UInt32`
  * `lds_size_per_local_work_group::UInt32`
  * `lds_usage_size_in_bytes::UInt64`
  * `scratch_mem_usage_in_bytes::UInt64`
