Arguments:

  * `device::Device`
  * `code_size::UInt`
  * `code::Vector{UInt32}`
  * `allocator::AllocationCallbacks`: defaults to `C_NULL`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateShaderModule.html)

```julia
ShaderModule(
    device,
    code_size::Integer,
    code::AbstractArray;
    allocator,
    next,
    flags
) -> Vulkan.ShaderModule

```
