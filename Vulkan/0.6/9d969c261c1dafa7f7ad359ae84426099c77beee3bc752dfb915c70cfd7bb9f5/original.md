Extension: VK_AMD_shader_core_properties

Arguments:

  * `shader_engine_count::UInt32`
  * `shader_arrays_per_engine_count::UInt32`
  * `compute_units_per_shader_array::UInt32`
  * `simd_per_compute_unit::UInt32`
  * `wavefronts_per_simd::UInt32`
  * `wavefront_size::UInt32`
  * `sgprs_per_simd::UInt32`
  * `min_sgpr_allocation::UInt32`
  * `max_sgpr_allocation::UInt32`
  * `sgpr_allocation_granularity::UInt32`
  * `vgprs_per_simd::UInt32`
  * `min_vgpr_allocation::UInt32`
  * `max_vgpr_allocation::UInt32`
  * `vgpr_allocation_granularity::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderCorePropertiesAMD.html)

```julia
_PhysicalDeviceShaderCorePropertiesAMD(
    shader_engine_count::Integer,
    shader_arrays_per_engine_count::Integer,
    compute_units_per_shader_array::Integer,
    simd_per_compute_unit::Integer,
    wavefronts_per_simd::Integer,
    wavefront_size::Integer,
    sgprs_per_simd::Integer,
    min_sgpr_allocation::Integer,
    max_sgpr_allocation::Integer,
    sgpr_allocation_granularity::Integer,
    vgprs_per_simd::Integer,
    min_vgpr_allocation::Integer,
    max_vgpr_allocation::Integer,
    vgpr_allocation_granularity::Integer;
    next
) -> Vulkan._PhysicalDeviceShaderCorePropertiesAMD

```
