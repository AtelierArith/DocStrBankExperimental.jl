拡張: VK*EXT*graphics*pipeline*library

引数:

  * `graphics_pipeline_library_fast_linking::Bool`
  * `graphics_pipeline_library_independent_interpolation_decoration::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceGraphicsPipelineLibraryPropertiesEXT.html)

```julia
_PhysicalDeviceGraphicsPipelineLibraryPropertiesEXT(
    graphics_pipeline_library_fast_linking::Bool,
    graphics_pipeline_library_independent_interpolation_decoration::Bool;
    next
) -> Vulkan._PhysicalDeviceGraphicsPipelineLibraryPropertiesEXT

```
