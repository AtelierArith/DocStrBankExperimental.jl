Extension: VK_NV_scissor_exclusive

Arguments:

  * `exclusive_scissors::Vector{_Rect2D}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportExclusiveScissorStateCreateInfoNV.html)

```julia
_PipelineViewportExclusiveScissorStateCreateInfoNV(
    exclusive_scissors::AbstractArray;
    next
) -> Vulkan._PipelineViewportExclusiveScissorStateCreateInfoNV

```
