引数:

  * `external_memory_features::ExternalMemoryFeatureFlag`
  * `compatible_handle_types::ExternalMemoryHandleTypeFlag`
  * `export_from_imported_handle_types::ExternalMemoryHandleTypeFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExternalMemoryProperties.html)

```julia
_ExternalMemoryProperties(
    external_memory_features::Vulkan.ExternalMemoryFeatureFlag,
    compatible_handle_types::Vulkan.ExternalMemoryHandleTypeFlag;
    export_from_imported_handle_types
) -> Vulkan._ExternalMemoryProperties

```
