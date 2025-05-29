Arguments:

  * `subresource::_ImageSubresource`
  * `offset::_Offset3D`
  * `extent::_Extent3D`
  * `memory_offset::UInt64`
  * `memory::DeviceMemory`: defaults to `C_NULL`
  * `flags::SparseMemoryBindFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseImageMemoryBind.html)

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
