Arguments:

  * `code_size::UInt`
  * `code::Vector{UInt32}`
  * `next::Any`: defaults to `C_NULL`
  * `flags::UInt32`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkShaderModuleCreateInfo.html)

```julia
ShaderModuleCreateInfo(
    code_size::Integer,
    code::AbstractArray;
    next,
    flags
) -> Vulkan.ShaderModuleCreateInfo

```
