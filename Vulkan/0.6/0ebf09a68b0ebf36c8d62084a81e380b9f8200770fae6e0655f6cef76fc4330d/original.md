Extension: VK_NV_dedicated_allocation

Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `image::Image`: defaults to `C_NULL`
  * `buffer::Buffer`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDedicatedAllocationMemoryAllocateInfoNV.html)

```julia
_DedicatedAllocationMemoryAllocateInfoNV(
;
    next,
    image,
    buffer
) -> Vulkan._DedicatedAllocationMemoryAllocateInfoNV

```
