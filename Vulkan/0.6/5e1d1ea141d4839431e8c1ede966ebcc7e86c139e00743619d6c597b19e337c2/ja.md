拡張: VK*AMD*shader*core*properties2

引数:

  * `shader_core_features::ShaderCorePropertiesFlagAMD`
  * `active_compute_unit_count::UInt32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderCoreProperties2AMD.html)

```julia
PhysicalDeviceShaderCoreProperties2AMD(
    shader_core_features::Vulkan.ShaderCorePropertiesFlagAMD,
    active_compute_unit_count::Integer;
    next
) -> Vulkan.PhysicalDeviceShaderCoreProperties2AMD

```
