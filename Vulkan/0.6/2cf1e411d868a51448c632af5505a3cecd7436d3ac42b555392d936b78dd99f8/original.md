Arguments:

  * `supported_depth_resolve_modes::ResolveModeFlag`
  * `supported_stencil_resolve_modes::ResolveModeFlag`
  * `independent_resolve_none::Bool`
  * `independent_resolve::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDepthStencilResolveProperties.html)

```julia
_PhysicalDeviceDepthStencilResolveProperties(
    supported_depth_resolve_modes::Vulkan.ResolveModeFlag,
    supported_stencil_resolve_modes::Vulkan.ResolveModeFlag,
    independent_resolve_none::Bool,
    independent_resolve::Bool;
    next
) -> Vulkan._PhysicalDeviceDepthStencilResolveProperties

```
