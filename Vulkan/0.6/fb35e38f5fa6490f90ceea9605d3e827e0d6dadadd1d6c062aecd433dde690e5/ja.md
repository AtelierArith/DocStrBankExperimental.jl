拡張: VK*NV*external_memory

引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `handle_types::ExternalMemoryHandleTypeFlagNV`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExportMemoryAllocateInfoNV.html)

```julia
_ExportMemoryAllocateInfoNV(
;
    next,
    handle_types
) -> Vulkan._ExportMemoryAllocateInfoNV

```
