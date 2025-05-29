引数:

  * `depth_resolve_mode::ResolveModeFlag`
  * `stencil_resolve_mode::ResolveModeFlag`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `depth_stencil_resolve_attachment::_AttachmentReference2`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubpassDescriptionDepthStencilResolve.html)

```julia
_SubpassDescriptionDepthStencilResolve(
    depth_resolve_mode::Vulkan.ResolveModeFlag,
    stencil_resolve_mode::Vulkan.ResolveModeFlag;
    next,
    depth_stencil_resolve_attachment
) -> Vulkan._SubpassDescriptionDepthStencilResolve

```
