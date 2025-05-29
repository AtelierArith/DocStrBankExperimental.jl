引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `image::Image`: デフォルトは `C_NULL`
  * `buffer::Buffer`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryDedicatedAllocateInfo.html)

```julia
_MemoryDedicatedAllocateInfo(
;
    next,
    image,
    buffer
) -> Vulkan._MemoryDedicatedAllocateInfo

```
