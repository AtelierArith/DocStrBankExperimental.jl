Extension: VK_AMD_shader_info

Arguments:

  * `num_used_vgprs::UInt32`
  * `num_used_sgprs::UInt32`
  * `lds_size_per_local_work_group::UInt32`
  * `lds_usage_size_in_bytes::UInt`
  * `scratch_mem_usage_in_bytes::UInt`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkShaderResourceUsageAMD.html)

```julia
_ShaderResourceUsageAMD(
    num_used_vgprs::Integer,
    num_used_sgprs::Integer,
    lds_size_per_local_work_group::Integer,
    lds_usage_size_in_bytes::Integer,
    scratch_mem_usage_in_bytes::Integer
) -> Vulkan._ShaderResourceUsageAMD

```
