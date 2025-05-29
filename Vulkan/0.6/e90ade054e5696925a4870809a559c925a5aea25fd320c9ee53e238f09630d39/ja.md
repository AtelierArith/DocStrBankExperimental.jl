引数:

  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `src_stage_mask::UInt64`: デフォルトは `0`
  * `src_access_mask::UInt64`: デフォルトは `0`
  * `dst_stage_mask::UInt64`: デフォルトは `0`
  * `dst_access_mask::UInt64`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryBarrier2.html)

```julia
_MemoryBarrier2(
;
    next,
    src_stage_mask,
    src_access_mask,
    dst_stage_mask,
    dst_access_mask
) -> Vulkan._MemoryBarrier2

```
