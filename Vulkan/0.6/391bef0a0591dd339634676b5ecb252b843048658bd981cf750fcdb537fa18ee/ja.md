引数:

  * `next::Any`: デフォルトは `C_NULL`
  * `src_access_mask::AccessFlag`: デフォルトは `0`
  * `dst_access_mask::AccessFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryBarrier.html)

```julia
MemoryBarrier(
;
    next,
    src_access_mask,
    dst_access_mask
) -> Vulkan.MemoryBarrier

```
