拡張: VK*NV*scissor_exclusive

引数:

  * `exclusive_scissors::Vector{Rect2D}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportExclusiveScissorStateCreateInfoNV.html)

```julia
PipelineViewportExclusiveScissorStateCreateInfoNV(
    exclusive_scissors::AbstractArray;
    next
) -> Vulkan.PipelineViewportExclusiveScissorStateCreateInfoNV

```
