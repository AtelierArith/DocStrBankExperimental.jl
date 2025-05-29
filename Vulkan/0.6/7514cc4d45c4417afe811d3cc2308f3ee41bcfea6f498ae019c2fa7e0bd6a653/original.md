Extension: VK_EXT_subpass_merge_feedback

Arguments:

  * `disallow_merging::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkRenderPassCreationControlEXT.html)

```julia
_RenderPassCreationControlEXT(
    disallow_merging::Bool;
    next
) -> Vulkan._RenderPassCreationControlEXT

```
