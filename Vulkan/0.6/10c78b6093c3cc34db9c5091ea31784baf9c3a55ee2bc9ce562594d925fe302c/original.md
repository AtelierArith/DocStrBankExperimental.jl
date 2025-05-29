Arguments:

  * `external_memory_features::ExternalMemoryFeatureFlag`
  * `compatible_handle_types::ExternalMemoryHandleTypeFlag`
  * `export_from_imported_handle_types::ExternalMemoryHandleTypeFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExternalMemoryProperties.html)

```julia
ExternalMemoryProperties(
    external_memory_features::Vulkan.ExternalMemoryFeatureFlag,
    compatible_handle_types::Vulkan.ExternalMemoryHandleTypeFlag;
    export_from_imported_handle_types
) -> Vulkan.ExternalMemoryProperties

```
