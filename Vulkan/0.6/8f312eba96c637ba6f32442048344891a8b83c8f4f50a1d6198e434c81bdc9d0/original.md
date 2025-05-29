Arguments:

  * `next::Ptr{Cvoid}`: defaults to `C_NULL`
  * `src_access_mask::AccessFlag`: defaults to `0`
  * `dst_access_mask::AccessFlag`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryBarrier.html)

```julia
_MemoryBarrier(
;
    next,
    src_access_mask,
    dst_access_mask
) -> Vulkan._MemoryBarrier

```
