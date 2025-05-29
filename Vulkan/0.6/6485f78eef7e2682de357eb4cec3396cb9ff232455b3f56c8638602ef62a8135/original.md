Extension: VK_NV_external_memory

Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `handle_types::ExternalMemoryHandleTypeFlagNV`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkExternalMemoryImageCreateInfoNV.html)

```julia
_ExternalMemoryImageCreateInfoNV(
;
    next,
    handle_types
) -> Vulkan._ExternalMemoryImageCreateInfoNV

```
