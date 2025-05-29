High-level wrapper for VkMemoryBarrier2.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkMemoryBarrier2.html)

```julia
struct MemoryBarrier2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_stage_mask::UInt64`
  * `src_access_mask::UInt64`
  * `dst_stage_mask::UInt64`
  * `dst_access_mask::UInt64`
