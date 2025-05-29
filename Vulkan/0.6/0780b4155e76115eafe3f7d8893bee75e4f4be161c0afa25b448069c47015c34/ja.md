拡張: VK*ARM*shader*core*builtins

引数:

  * `shader_core_mask::UInt64`
  * `shader_core_count::UInt32`
  * `shader_warps_per_core::UInt32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderCoreBuiltinsPropertiesARM.html)

```julia
PhysicalDeviceShaderCoreBuiltinsPropertiesARM(
    shader_core_mask::Integer,
    shader_core_count::Integer,
    shader_warps_per_core::Integer;
    next
) -> Vulkan.PhysicalDeviceShaderCoreBuiltinsPropertiesARM

```
