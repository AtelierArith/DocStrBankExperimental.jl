High-level wrapper for VkExternalImageFormatPropertiesNV.

Extension: VK_NV_external_memory_capabilities

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExternalImageFormatPropertiesNV.html)

```julia
struct ExternalImageFormatPropertiesNV <: Vulkan.HighLevelStruct
```

  * `image_format_properties::Vulkan.ImageFormatProperties`
  * `external_memory_features::Vulkan.ExternalMemoryFeatureFlagNV`
  * `export_from_imported_handle_types::Vulkan.ExternalMemoryHandleTypeFlagNV`
  * `compatible_handle_types::Vulkan.ExternalMemoryHandleTypeFlagNV`
