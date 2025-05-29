Arguments:

  * `shader_buffer_int_64_atomics::Bool`
  * `shader_shared_int_64_atomics::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceShaderAtomicInt64Features.html)

```julia
_PhysicalDeviceShaderAtomicInt64Features(
    shader_buffer_int_64_atomics::Bool,
    shader_shared_int_64_atomics::Bool;
    next
) -> Vulkan._PhysicalDeviceShaderAtomicInt64Features

```
