引数:

  * `denorm_behavior_independence::ShaderFloatControlsIndependence`
  * `rounding_mode_independence::ShaderFloatControlsIndependence`
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
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceFloatControlsProperties.html)

```julia
_PhysicalDeviceFloatControlsProperties(
    denorm_behavior_independence::Vulkan.ShaderFloatControlsIndependence,
    rounding_mode_independence::Vulkan.ShaderFloatControlsIndependence,
    shader_signed_zero_inf_nan_preserve_float_16::Bool,
    shader_signed_zero_inf_nan_preserve_float_32::Bool,
    shader_signed_zero_inf_nan_preserve_float_64::Bool,
    shader_denorm_preserve_float_16::Bool,
    shader_denorm_preserve_float_32::Bool,
    shader_denorm_preserve_float_64::Bool,
    shader_denorm_flush_to_zero_float_16::Bool,
    shader_denorm_flush_to_zero_float_32::Bool,
    shader_denorm_flush_to_zero_float_64::Bool,
    shader_rounding_mode_rte_float_16::Bool,
    shader_rounding_mode_rte_float_32::Bool,
    shader_rounding_mode_rte_float_64::Bool,
    shader_rounding_mode_rtz_float_16::Bool,
    shader_rounding_mode_rtz_float_32::Bool,
    shader_rounding_mode_rtz_float_64::Bool;
    next
) -> Vulkan._PhysicalDeviceFloatControlsProperties

```
