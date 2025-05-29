Extension: VK_NV_shader_sm_builtins

Arguments:

  * `shader_sm_count::UInt32`
  * `shader_warps_per_sm::UInt32`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderSMBuiltinsPropertiesNV.html)

```julia
PhysicalDeviceShaderSMBuiltinsPropertiesNV(
    shader_sm_count::Integer,
    shader_warps_per_sm::Integer;
    next
) -> Vulkan.PhysicalDeviceShaderSMBuiltinsPropertiesNV

```
