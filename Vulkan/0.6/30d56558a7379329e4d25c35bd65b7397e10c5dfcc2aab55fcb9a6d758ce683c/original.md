Extension: VK_EXT_shader_image_atomic_int64

Arguments:

  * `shader_image_int_64_atomics::Bool`
  * `sparse_image_int_64_atomics::Bool`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderImageAtomicInt64FeaturesEXT.html)

```julia
PhysicalDeviceShaderImageAtomicInt64FeaturesEXT(
    shader_image_int_64_atomics::Bool,
    sparse_image_int_64_atomics::Bool;
    next
) -> Vulkan.PhysicalDeviceShaderImageAtomicInt64FeaturesEXT

```
