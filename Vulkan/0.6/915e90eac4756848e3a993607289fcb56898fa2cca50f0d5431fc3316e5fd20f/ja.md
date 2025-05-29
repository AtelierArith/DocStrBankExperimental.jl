引数:

  * `export_from_imported_handle_types::ExternalSemaphoreHandleTypeFlag`
  * `compatible_handle_types::ExternalSemaphoreHandleTypeFlag`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `external_semaphore_features::ExternalSemaphoreFeatureFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExternalSemaphoreProperties.html)

```julia
_ExternalSemaphoreProperties(
    export_from_imported_handle_types::Vulkan.ExternalSemaphoreHandleTypeFlag,
    compatible_handle_types::Vulkan.ExternalSemaphoreHandleTypeFlag;
    next,
    external_semaphore_features
) -> Vulkan._ExternalSemaphoreProperties

```
