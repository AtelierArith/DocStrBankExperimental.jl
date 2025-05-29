引数:

  * `device::Device`
  * `code_size::UInt`
  * `code::Vector{UInt32}`
  * `allocator::AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateShaderModule.html)

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
