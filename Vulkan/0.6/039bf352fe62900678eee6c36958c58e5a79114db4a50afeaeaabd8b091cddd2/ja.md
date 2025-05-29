引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `handle_types::ExternalFenceHandleTypeFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExportFenceCreateInfo.html)

```julia
_ExportFenceCreateInfo(
;
    next,
    handle_types
) -> Vulkan._ExportFenceCreateInfo

```
