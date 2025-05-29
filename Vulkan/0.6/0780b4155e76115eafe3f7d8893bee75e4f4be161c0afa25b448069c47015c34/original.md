Extension: VK_ARM_shader_core_builtins

Arguments:

  * `shader_core_mask::UInt64`
  * `shader_core_count::UInt32`
  * `shader_warps_per_core::UInt32`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderCoreBuiltinsPropertiesARM.html)

```julia
PhysicalDeviceShaderCoreBuiltinsPropertiesARM(
    shader_core_mask::Integer,
    shader_core_count::Integer,
    shader_warps_per_core::Integer;
    next
) -> Vulkan.PhysicalDeviceShaderCoreBuiltinsPropertiesARM

```
