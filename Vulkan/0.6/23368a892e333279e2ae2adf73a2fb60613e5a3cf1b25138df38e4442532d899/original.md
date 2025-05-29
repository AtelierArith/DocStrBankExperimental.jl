Extension: VK_EXT_external_memory_host

Arguments:

  * `memory_type_bits::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryHostPointerPropertiesEXT.html)

```julia
_MemoryHostPointerPropertiesEXT(
    memory_type_bits::Integer;
    next
) -> Vulkan._MemoryHostPointerPropertiesEXT

```
