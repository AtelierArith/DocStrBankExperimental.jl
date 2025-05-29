Arguments:

  * `depth_resolve_mode::ResolveModeFlag`
  * `stencil_resolve_mode::ResolveModeFlag`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `depth_stencil_resolve_attachment::_AttachmentReference2`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubpassDescriptionDepthStencilResolve.html)

```julia
_SubpassDescriptionDepthStencilResolve(
    depth_resolve_mode::Vulkan.ResolveModeFlag,
    stencil_resolve_mode::Vulkan.ResolveModeFlag;
    next,
    depth_stencil_resolve_attachment
) -> Vulkan._SubpassDescriptionDepthStencilResolve

```
