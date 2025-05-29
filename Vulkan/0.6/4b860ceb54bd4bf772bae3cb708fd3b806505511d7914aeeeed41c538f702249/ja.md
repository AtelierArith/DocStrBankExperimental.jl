VkPhysicalDeviceShaderAtomicFloatFeaturesEXTの高レベルラッパー。

拡張: VK*EXT*shader*atomic*float

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderAtomicFloatFeaturesEXT.html)

```julia
struct PhysicalDeviceShaderAtomicFloatFeaturesEXT <: Vulkan.HighLevelStruct
```

  * `next::Any`
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
