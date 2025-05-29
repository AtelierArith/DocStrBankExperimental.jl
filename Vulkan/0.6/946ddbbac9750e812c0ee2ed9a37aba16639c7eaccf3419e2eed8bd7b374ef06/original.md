High-level wrapper for VkSubpassDescriptionDepthStencilResolve.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSubpassDescriptionDepthStencilResolve.html)

```julia
struct SubpassDescriptionDepthStencilResolve <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `depth_resolve_mode::Vulkan.ResolveModeFlag`
  * `stencil_resolve_mode::Vulkan.ResolveModeFlag`
  * `depth_stencil_resolve_attachment::Union{Ptr{Nothing}, Vulkan.AttachmentReference2}`
