Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `handle_types::ExternalSemaphoreHandleTypeFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExportSemaphoreCreateInfo.html)

```julia
_ExportSemaphoreCreateInfo(
;
    next,
    handle_types
) -> Vulkan._ExportSemaphoreCreateInfo

```
