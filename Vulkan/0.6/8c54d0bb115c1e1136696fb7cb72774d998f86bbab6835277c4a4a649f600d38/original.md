Extension: VK_HUAWEI_subpass_shading

Arguments:

  * `render_pass::RenderPass`
  * `subpass::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubpassShadingPipelineCreateInfoHUAWEI.html)

```julia
_SubpassShadingPipelineCreateInfoHUAWEI(
    render_pass,
    subpass::Integer;
    next
) -> Vulkan._SubpassShadingPipelineCreateInfoHUAWEI

```
