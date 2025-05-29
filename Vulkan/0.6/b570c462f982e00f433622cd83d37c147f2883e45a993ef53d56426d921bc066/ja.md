拡張: VK*NV*device*generated*commands

引数:

  * `groups::Vector{GraphicsShaderGroupCreateInfoNV}`
  * `pipelines::Vector{Pipeline}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsPipelineShaderGroupsCreateInfoNV.html)

```julia
GraphicsPipelineShaderGroupsCreateInfoNV(
    groups::AbstractArray,
    pipelines::AbstractArray;
    next
) -> Vulkan.GraphicsPipelineShaderGroupsCreateInfoNV

```
