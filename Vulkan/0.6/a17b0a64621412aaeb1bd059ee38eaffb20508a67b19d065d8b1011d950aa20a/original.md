Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `handle_types::ExternalMemoryHandleTypeFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExportMemoryAllocateInfo.html)

```julia
_ExportMemoryAllocateInfo(
;
    next,
    handle_types
) -> Vulkan._ExportMemoryAllocateInfo

```
