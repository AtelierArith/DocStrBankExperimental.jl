High-level wrapper for VkPhysicalDeviceShaderCorePropertiesAMD.

Extension: VK_AMD_shader_core_properties

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderCorePropertiesAMD.html)

```julia
struct PhysicalDeviceShaderCorePropertiesAMD <: Vulkan.HighLevelStruct
```

  * `next::Any`
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
