拡張: VK*NV*scissor_exclusive

引数:

  * `exclusive_scissors::Vector{_Rect2D}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPipelineViewportExclusiveScissorStateCreateInfoNV.html)

```julia
_PipelineViewportExclusiveScissorStateCreateInfoNV(
    exclusive_scissors::AbstractArray;
    next
) -> Vulkan._PipelineViewportExclusiveScissorStateCreateInfoNV

```
