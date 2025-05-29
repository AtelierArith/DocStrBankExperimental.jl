引数:

  * `resource_offset::UInt64`
  * `size::UInt64`
  * `memory_offset::UInt64`
  * `memory::DeviceMemory`: デフォルトは `C_NULL`
  * `flags::SparseMemoryBindFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseMemoryBind.html)

```julia
_SparseMemoryBind(
    resource_offset::Integer,
    size::Integer,
    memory_offset::Integer;
    memory,
    flags
) -> Vulkan._SparseMemoryBind

```
