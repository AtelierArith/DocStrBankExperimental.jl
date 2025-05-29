拡張: VK*NV*dedicated_allocation

引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `image::Image`: デフォルトは `C_NULL`
  * `buffer::Buffer`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDedicatedAllocationMemoryAllocateInfoNV.html)

```julia
_DedicatedAllocationMemoryAllocateInfoNV(
;
    next,
    image,
    buffer
) -> Vulkan._DedicatedAllocationMemoryAllocateInfoNV

```
