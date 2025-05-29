引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `handle_types::ExternalSemaphoreHandleTypeFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExportSemaphoreCreateInfo.html)

```julia
_ExportSemaphoreCreateInfo(
;
    next,
    handle_types
) -> Vulkan._ExportSemaphoreCreateInfo

```
