Extension: VK_EXT_shader_atomic_float

Arguments:

  * `shader_buffer_float_32_atomics::Bool`
  * `shader_buffer_float_32_atomic_add::Bool`
  * `shader_buffer_float_64_atomics::Bool`
  * `shader_buffer_float_64_atomic_add::Bool`
  * `shader_shared_float_32_atomics::Bool`
  * `shader_shared_float_32_atomic_add::Bool`
  * `shader_shared_float_64_atomics::Bool`
  * `shader_shared_float_64_atomic_add::Bool`
  * `shader_image_float_32_atomics::Bool`
  * `shader_image_float_32_atomic_add::Bool`
  * `sparse_image_float_32_atomics::Bool`
  * `sparse_image_float_32_atomic_add::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderAtomicFloatFeaturesEXT.html)

```julia
_PhysicalDeviceShaderAtomicFloatFeaturesEXT(
    shader_buffer_float_32_atomics::Bool,
    shader_buffer_float_32_atomic_add::Bool,
    shader_buffer_float_64_atomics::Bool,
    shader_buffer_float_64_atomic_add::Bool,
    shader_shared_float_32_atomics::Bool,
    shader_shared_float_32_atomic_add::Bool,
    shader_shared_float_64_atomics::Bool,
    shader_shared_float_64_atomic_add::Bool,
    shader_image_float_32_atomics::Bool,
    shader_image_float_32_atomic_add::Bool,
    sparse_image_float_32_atomics::Bool,
    sparse_image_float_32_atomic_add::Bool;
    next
) -> Vulkan._PhysicalDeviceShaderAtomicFloatFeaturesEXT

```
