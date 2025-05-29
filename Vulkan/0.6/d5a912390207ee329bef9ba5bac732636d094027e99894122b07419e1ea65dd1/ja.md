拡張: VK*EXT*external*memory*host

引数:

  * `handle_type::ExternalMemoryHandleTypeFlag`
  * `host_pointer::Ptr{Cvoid}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportMemoryHostPointerInfoEXT.html)

```julia
_ImportMemoryHostPointerInfoEXT(
    handle_type::Vulkan.ExternalMemoryHandleTypeFlag,
    host_pointer::Ptr{Nothing};
    next
) -> Vulkan._ImportMemoryHostPointerInfoEXT

```
