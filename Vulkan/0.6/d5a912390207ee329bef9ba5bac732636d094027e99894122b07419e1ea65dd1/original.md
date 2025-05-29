Extension: VK_EXT_external_memory_host

Arguments:

  * `handle_type::ExternalMemoryHandleTypeFlag`
  * `host_pointer::Ptr{Cvoid}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImportMemoryHostPointerInfoEXT.html)

```julia
_ImportMemoryHostPointerInfoEXT(
    handle_type::Vulkan.ExternalMemoryHandleTypeFlag,
    host_pointer::Ptr{Nothing};
    next
) -> Vulkan._ImportMemoryHostPointerInfoEXT

```
