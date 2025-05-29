Return codes:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_SHADER_NV`

Arguments:

  * `device::Device`
  * `code_size::UInt`
  * `code::Vector{UInt32}`
  * `allocator::_AllocationCallbacks`: defaults to `C_NULL`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateShaderModule.html)

```julia
_create_shader_module(
    device,
    code_size::Integer,
    code::AbstractArray;
    allocator,
    next,
    flags
) -> ResultTypes.Result{Vulkan.ShaderModule, Vulkan.VulkanError}

```
