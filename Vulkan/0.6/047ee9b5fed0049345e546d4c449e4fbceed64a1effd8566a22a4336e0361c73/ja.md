引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `handle_types::ExternalMemoryHandleTypeFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExternalMemoryImageCreateInfo.html)

```julia
_ExternalMemoryImageCreateInfo(
;
    next,
    handle_types
) -> Vulkan._ExternalMemoryImageCreateInfo

```
