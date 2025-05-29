High-level wrapper for VkPhysicalDeviceShaderCoreBuiltinsPropertiesARM.

Extension: VK_ARM_shader_core_builtins

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderCoreBuiltinsPropertiesARM.html)

```julia
struct PhysicalDeviceShaderCoreBuiltinsPropertiesARM <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `shader_core_mask::UInt64`
  * `shader_core_count::UInt32`
  * `shader_warps_per_core::UInt32`
