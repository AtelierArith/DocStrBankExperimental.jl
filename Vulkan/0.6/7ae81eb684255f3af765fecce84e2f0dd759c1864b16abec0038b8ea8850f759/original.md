Extension: VK_NV_scissor_exclusive

Arguments:

  * `exclusive_scissors::Vector{Rect2D}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportExclusiveScissorStateCreateInfoNV.html)

```julia
PipelineViewportExclusiveScissorStateCreateInfoNV(
    exclusive_scissors::AbstractArray;
    next
) -> Vulkan.PipelineViewportExclusiveScissorStateCreateInfoNV

```
