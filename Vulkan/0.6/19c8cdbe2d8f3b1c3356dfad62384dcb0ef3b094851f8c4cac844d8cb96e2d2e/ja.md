引数:

  * `subresource::_ImageSubresource`
  * `offset::_Offset3D`
  * `extent::_Extent3D`
  * `memory_offset::UInt64`
  * `memory::DeviceMemory`: デフォルトは `C_NULL`
  * `flags::SparseMemoryBindFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseImageMemoryBind.html)

```julia
_SparseImageMemoryBind(
    subresource::Vulkan._ImageSubresource,
    offset::Vulkan._Offset3D,
    extent::Vulkan._Extent3D,
    memory_offset::Integer;
    memory,
    flags
) -> Vulkan._SparseImageMemoryBind

```
