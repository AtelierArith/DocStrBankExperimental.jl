VkExternalSemaphorePropertiesの高レベルラッパー。

[APIドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExternalSemaphoreProperties.html)

```julia
struct ExternalSemaphoreProperties <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `export_from_imported_handle_types::Vulkan.ExternalSemaphoreHandleTypeFlag`
  * `compatible_handle_types::Vulkan.ExternalSemaphoreHandleTypeFlag`
  * `external_semaphore_features::Vulkan.ExternalSemaphoreFeatureFlag`
