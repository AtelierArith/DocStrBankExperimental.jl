High-level wrapper for VkPhysicalDeviceFloatControlsProperties.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFloatControlsProperties.html)

```julia
struct PhysicalDeviceFloatControlsProperties <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `denorm_behavior_independence::Vulkan.ShaderFloatControlsIndependence`
  * `rounding_mode_independence::Vulkan.ShaderFloatControlsIndependence`
  * `shader_signed_zero_inf_nan_preserve_float_16::Bool`
  * `shader_signed_zero_inf_nan_preserve_float_32::Bool`
  * `shader_signed_zero_inf_nan_preserve_float_64::Bool`
  * `shader_denorm_preserve_float_16::Bool`
  * `shader_denorm_preserve_float_32::Bool`
  * `shader_denorm_preserve_float_64::Bool`
  * `shader_denorm_flush_to_zero_float_16::Bool`
  * `shader_denorm_flush_to_zero_float_32::Bool`
  * `shader_denorm_flush_to_zero_float_64::Bool`
  * `shader_rounding_mode_rte_float_16::Bool`
  * `shader_rounding_mode_rte_float_32::Bool`
  * `shader_rounding_mode_rte_float_64::Bool`
  * `shader_rounding_mode_rtz_float_16::Bool`
  * `shader_rounding_mode_rtz_float_32::Bool`
  * `shader_rounding_mode_rtz_float_64::Bool`
