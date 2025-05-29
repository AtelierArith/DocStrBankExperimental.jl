拡張: VK*EXT*external*memory*host

引数:

  * `memory_type_bits::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryHostPointerPropertiesEXT.html)

```julia
_MemoryHostPointerPropertiesEXT(
    memory_type_bits::Integer;
    next
) -> Vulkan._MemoryHostPointerPropertiesEXT

```
