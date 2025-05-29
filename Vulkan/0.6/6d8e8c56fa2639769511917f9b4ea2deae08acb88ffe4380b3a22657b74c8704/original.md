High-level wrapper for VkImageMemoryBarrier2.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageMemoryBarrier2.html)

```julia
struct ImageMemoryBarrier2 <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_stage_mask::UInt64`
  * `src_access_mask::UInt64`
  * `dst_stage_mask::UInt64`
  * `dst_access_mask::UInt64`
  * `old_layout::Vulkan.ImageLayout`
  * `new_layout::Vulkan.ImageLayout`
  * `src_queue_family_index::UInt32`
  * `dst_queue_family_index::UInt32`
  * `image::Vulkan.Image`
  * `subresource_range::Vulkan.ImageSubresourceRange`
