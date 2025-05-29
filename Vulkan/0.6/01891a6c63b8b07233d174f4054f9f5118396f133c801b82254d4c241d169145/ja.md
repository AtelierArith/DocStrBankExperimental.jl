引数:

  * `code_size::UInt`
  * `code::Vector{UInt32}`
  * `next::Any`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkShaderModuleCreateInfo.html)

```julia
ShaderModuleCreateInfo(
    code_size::Integer,
    code::AbstractArray;
    next,
    flags
) -> Vulkan.ShaderModuleCreateInfo

```
