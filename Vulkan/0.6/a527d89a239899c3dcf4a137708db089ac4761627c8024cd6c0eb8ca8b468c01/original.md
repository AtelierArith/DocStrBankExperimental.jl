High-level wrapper for VkPhysicalDeviceShaderAtomicFloat2FeaturesEXT.

Extension: VK_EXT_shader_atomic_float2

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderAtomicFloat2FeaturesEXT.html)

```julia
struct PhysicalDeviceShaderAtomicFloat2FeaturesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `shader_buffer_float_16_atomics::Bool`
  * `shader_buffer_float_16_atomic_add::Bool`
  * `shader_buffer_float_16_atomic_min_max::Bool`
  * `shader_buffer_float_32_atomic_min_max::Bool`
  * `shader_buffer_float_64_atomic_min_max::Bool`
  * `shader_shared_float_16_atomics::Bool`
  * `shader_shared_float_16_atomic_add::Bool`
  * `shader_shared_float_16_atomic_min_max::Bool`
  * `shader_shared_float_32_atomic_min_max::Bool`
  * `shader_shared_float_64_atomic_min_max::Bool`
  * `shader_image_float_32_atomic_min_max::Bool`
  * `sparse_image_float_32_atomic_min_max::Bool`
