引数:

  * `shader_buffer_int_64_atomics::Bool`
  * `shader_shared_int_64_atomics::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderAtomicInt64Features.html)

```julia
_PhysicalDeviceShaderAtomicInt64Features(
    shader_buffer_int_64_atomics::Bool,
    shader_shared_int_64_atomics::Bool;
    next
) -> Vulkan._PhysicalDeviceShaderAtomicInt64Features

```
