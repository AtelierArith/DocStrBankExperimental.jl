拡張: VK*EXT*shader*module*identifier

引数:

  * `identifier::Vector{UInt8}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `identifier_size::UInt32`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineShaderStageModuleIdentifierCreateInfoEXT.html)

```julia
_PipelineShaderStageModuleIdentifierCreateInfoEXT(
    identifier::AbstractArray;
    next,
    identifier_size
) -> Vulkan._PipelineShaderStageModuleIdentifierCreateInfoEXT

```
