VkPhysicalDeviceDepthStencilResolvePropertiesの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceDepthStencilResolveProperties.html)

```julia
struct PhysicalDeviceDepthStencilResolveProperties <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `supported_depth_resolve_modes::Vulkan.ResolveModeFlag`
  * `supported_stencil_resolve_modes::Vulkan.ResolveModeFlag`
  * `independent_resolve_none::Bool`
  * `independent_resolve::Bool`
