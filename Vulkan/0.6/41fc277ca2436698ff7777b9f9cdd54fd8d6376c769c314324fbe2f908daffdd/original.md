High-level wrapper for VkImageMemoryBarrier.

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageMemoryBarrier.html)

```julia
struct ImageMemoryBarrier <: Vulkan.HighLevelStruct
```

  * `next::Any`
  * `src_access_mask::Vulkan.AccessFlag`
  * `dst_access_mask::Vulkan.AccessFlag`
  * `old_layout::Vulkan.ImageLayout`
  * `new_layout::Vulkan.ImageLayout`
  * `src_queue_family_index::UInt32`
  * `dst_queue_family_index::UInt32`
  * `image::Vulkan.Image`
  * `subresource_range::Vulkan.ImageSubresourceRange`
