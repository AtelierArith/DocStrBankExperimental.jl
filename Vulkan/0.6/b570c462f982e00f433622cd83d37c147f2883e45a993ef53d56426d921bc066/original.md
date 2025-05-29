Extension: VK_NV_device_generated_commands

Arguments:

  * `groups::Vector{GraphicsShaderGroupCreateInfoNV}`
  * `pipelines::Vector{Pipeline}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkGraphicsPipelineShaderGroupsCreateInfoNV.html)

```julia
GraphicsPipelineShaderGroupsCreateInfoNV(
    groups::AbstractArray,
    pipelines::AbstractArray;
    next
) -> Vulkan.GraphicsPipelineShaderGroupsCreateInfoNV

```
