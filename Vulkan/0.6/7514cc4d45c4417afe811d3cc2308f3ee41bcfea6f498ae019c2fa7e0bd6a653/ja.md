拡張: VK*EXT*subpass*merge*feedback

引数:

  * `disallow_merging::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassCreationControlEXT.html)

```julia
_RenderPassCreationControlEXT(
    disallow_merging::Bool;
    next
) -> Vulkan._RenderPassCreationControlEXT

```
