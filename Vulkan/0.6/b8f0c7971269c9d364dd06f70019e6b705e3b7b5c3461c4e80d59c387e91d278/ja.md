引数:

  * `export_from_imported_handle_types::ExternalFenceHandleTypeFlag`
  * `compatible_handle_types::ExternalFenceHandleTypeFlag`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `external_fence_features::ExternalFenceFeatureFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExternalFenceProperties.html)

```julia
_ExternalFenceProperties(
    export_from_imported_handle_types::Vulkan.ExternalFenceHandleTypeFlag,
    compatible_handle_types::Vulkan.ExternalFenceHandleTypeFlag;
    next,
    external_fence_features
) -> Vulkan._ExternalFenceProperties

```
