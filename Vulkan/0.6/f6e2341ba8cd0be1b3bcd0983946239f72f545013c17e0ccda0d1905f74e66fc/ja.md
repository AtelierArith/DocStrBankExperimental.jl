拡張: VK*EXT*shader*atomic*float2

引数:

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
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderAtomicFloat2FeaturesEXT.html)

```julia
PhysicalDeviceShaderAtomicFloat2FeaturesEXT(
    shader_buffer_float_16_atomics::Bool,
    shader_buffer_float_16_atomic_add::Bool,
    shader_buffer_float_16_atomic_min_max::Bool,
    shader_buffer_float_32_atomic_min_max::Bool,
    shader_buffer_float_64_atomic_min_max::Bool,
    shader_shared_float_16_atomics::Bool,
    shader_shared_float_16_atomic_add::Bool,
    shader_shared_float_16_atomic_min_max::Bool,
    shader_shared_float_32_atomic_min_max::Bool,
    shader_shared_float_64_atomic_min_max::Bool,
    shader_image_float_32_atomic_min_max::Bool,
    sparse_image_float_32_atomic_min_max::Bool;
    next
) -> Vulkan.PhysicalDeviceShaderAtomicFloat2FeaturesEXT

```
