VkExternalImageFormatPropertiesNVの高レベルラッパー。

拡張: VK*NV*external*memory*capabilities

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExternalImageFormatPropertiesNV.html)

```julia
struct ExternalImageFormatPropertiesNV <: Vulkan.HighLevelStruct
```

  * `image_format_properties::Vulkan.ImageFormatProperties`
  * `external_memory_features::Vulkan.ExternalMemoryFeatureFlagNV`
  * `export_from_imported_handle_types::Vulkan.ExternalMemoryHandleTypeFlagNV`
  * `compatible_handle_types::Vulkan.ExternalMemoryHandleTypeFlagNV`
