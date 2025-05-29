拡張: VK*NV*shader*sm*builtins

引数:

  * `shader_sm_count::UInt32`
  * `shader_warps_per_sm::UInt32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderSMBuiltinsPropertiesNV.html)

```julia
PhysicalDeviceShaderSMBuiltinsPropertiesNV(
    shader_sm_count::Integer,
    shader_warps_per_sm::Integer;
    next
) -> Vulkan.PhysicalDeviceShaderSMBuiltinsPropertiesNV

```
