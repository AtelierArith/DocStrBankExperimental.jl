引数:

  * `supported_depth_resolve_modes::ResolveModeFlag`
  * `supported_stencil_resolve_modes::ResolveModeFlag`
  * `independent_resolve_none::Bool`
  * `independent_resolve::Bool`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDepthStencilResolveProperties.html)

```julia
PhysicalDeviceDepthStencilResolveProperties(
    supported_depth_resolve_modes::Vulkan.ResolveModeFlag,
    supported_stencil_resolve_modes::Vulkan.ResolveModeFlag,
    independent_resolve_none::Bool,
    independent_resolve::Bool;
    next
) -> Vulkan.PhysicalDeviceDepthStencilResolveProperties

```
