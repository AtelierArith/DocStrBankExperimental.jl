Arguments:

  * `next::Any`: defaults to `C_NULL`
  * `src_stage_mask::UInt64`: defaults to `0`
  * `src_access_mask::UInt64`: defaults to `0`
  * `dst_stage_mask::UInt64`: defaults to `0`
  * `dst_access_mask::UInt64`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryBarrier2.html)

```julia
MemoryBarrier2(
;
    next,
    src_stage_mask,
    src_access_mask,
    dst_stage_mask,
    dst_access_mask
) -> Vulkan.MemoryBarrier2

```
