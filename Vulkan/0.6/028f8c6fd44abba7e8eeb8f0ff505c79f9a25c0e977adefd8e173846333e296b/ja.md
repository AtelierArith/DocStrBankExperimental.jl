VkExternalMemoryPropertiesの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExternalMemoryProperties.html)

```julia
struct ExternalMemoryProperties <: Vulkan.HighLevelStruct
```

  * `external_memory_features::Vulkan.ExternalMemoryFeatureFlag`
  * `export_from_imported_handle_types::Vulkan.ExternalMemoryHandleTypeFlag`
  * `compatible_handle_types::Vulkan.ExternalMemoryHandleTypeFlag`
