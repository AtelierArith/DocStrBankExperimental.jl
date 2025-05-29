High-level wrapper for VkExternalFenceProperties.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExternalFenceProperties.html)

```julia
struct ExternalFenceProperties <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `export_from_imported_handle_types::Vulkan.ExternalFenceHandleTypeFlag`
  * `compatible_handle_types::Vulkan.ExternalFenceHandleTypeFlag`
  * `external_fence_features::Vulkan.ExternalFenceFeatureFlag`
