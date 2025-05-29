引数:

  * `code_size::UInt`
  * `code::Vector{UInt32}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkShaderModuleCreateInfo.html)

```julia
_ShaderModuleCreateInfo(
    code_size::Integer,
    code::AbstractArray;
    next,
    flags
) -> Vulkan._ShaderModuleCreateInfo

```
