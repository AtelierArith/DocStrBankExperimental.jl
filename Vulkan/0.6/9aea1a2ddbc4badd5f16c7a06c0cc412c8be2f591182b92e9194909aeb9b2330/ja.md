拡張: VK*EXT*conditional_rendering

引数:

  * `conditional_rendering_enable::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkCommandBufferInheritanceConditionalRenderingInfoEXT.html)

```julia
_CommandBufferInheritanceConditionalRenderingInfoEXT(
    conditional_rendering_enable::Bool;
    next
) -> Vulkan._CommandBufferInheritanceConditionalRenderingInfoEXT

```
