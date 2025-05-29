引数:

  * `allocation_size::UInt64`
  * `memory_type_index::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryAllocateInfo.html)

```julia
_MemoryAllocateInfo(
    allocation_size::Integer,
    memory_type_index::Integer;
    next
) -> Vulkan._MemoryAllocateInfo

```
