引数:

  * `subresource::ImageSubresource`
  * `offset::Offset3D`
  * `extent::Extent3D`
  * `memory_offset::UInt64`
  * `memory::DeviceMemory`: デフォルトは `C_NULL`
  * `flags::SparseMemoryBindFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSparseImageMemoryBind.html)

```julia
SparseImageMemoryBind(
    subresource::Vulkan.ImageSubresource,
    offset::Vulkan.Offset3D,
    extent::Vulkan.Extent3D,
    memory_offset::Integer;
    memory,
    flags
) -> Vulkan.SparseImageMemoryBind

```
