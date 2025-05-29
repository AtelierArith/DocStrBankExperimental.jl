戻り値:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INVALID_SHADER_NV`

引数:

  * `device::Device`
  * `code_size::UInt`
  * `code::Vector{UInt32}`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateShaderModule.html)

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
