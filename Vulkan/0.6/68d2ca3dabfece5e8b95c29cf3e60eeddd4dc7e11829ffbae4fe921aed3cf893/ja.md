拡張: VK*NV*device*generated*commands

引数:

  * `groups::Vector{_GraphicsShaderGroupCreateInfoNV}`
  * `pipelines::Vector{Pipeline}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsPipelineShaderGroupsCreateInfoNV.html)

```julia
_GraphicsPipelineShaderGroupsCreateInfoNV(
    groups::AbstractArray,
    pipelines::AbstractArray;
    next
) -> Vulkan._GraphicsPipelineShaderGroupsCreateInfoNV

```
