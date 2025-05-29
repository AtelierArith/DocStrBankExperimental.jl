拡張: VK*EXT*shader*image*atomic_int64

引数:

  * `shader_image_int_64_atomics::Bool`
  * `sparse_image_int_64_atomics::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderImageAtomicInt64FeaturesEXT.html)

```julia
_PhysicalDeviceShaderImageAtomicInt64FeaturesEXT(
    shader_image_int_64_atomics::Bool,
    sparse_image_int_64_atomics::Bool;
    next
) -> Vulkan._PhysicalDeviceShaderImageAtomicInt64FeaturesEXT

```
