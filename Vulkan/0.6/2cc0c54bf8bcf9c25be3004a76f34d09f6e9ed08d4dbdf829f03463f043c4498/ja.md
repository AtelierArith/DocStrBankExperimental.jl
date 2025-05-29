拡張: VK*NV*external*memory*capabilities

引数:

  * `image_format_properties::_ImageFormatProperties`
  * `external_memory_features::ExternalMemoryFeatureFlagNV`: デフォルトは `0`
  * `export_from_imported_handle_types::ExternalMemoryHandleTypeFlagNV`: デフォルトは `0`
  * `compatible_handle_types::ExternalMemoryHandleTypeFlagNV`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExternalImageFormatPropertiesNV.html)

```julia
_ExternalImageFormatPropertiesNV(
    image_format_properties::Vulkan._ImageFormatProperties;
    external_memory_features,
    export_from_imported_handle_types,
    compatible_handle_types
) -> Vulkan._ExternalImageFormatPropertiesNV

```
