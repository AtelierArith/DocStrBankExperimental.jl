Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `handle_types::ExternalFenceHandleTypeFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExportFenceCreateInfo.html)

```julia
_ExportFenceCreateInfo(
;
    next,
    handle_types
) -> Vulkan._ExportFenceCreateInfo

```
