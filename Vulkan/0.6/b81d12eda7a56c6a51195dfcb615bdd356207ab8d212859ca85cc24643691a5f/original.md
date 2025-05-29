Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `image::Image`: defaults to `C_NULL`
  * `buffer::Buffer`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryDedicatedAllocateInfo.html)

```julia
_MemoryDedicatedAllocateInfo(
;
    next,
    image,
    buffer
) -> Vulkan._MemoryDedicatedAllocateInfo

```
