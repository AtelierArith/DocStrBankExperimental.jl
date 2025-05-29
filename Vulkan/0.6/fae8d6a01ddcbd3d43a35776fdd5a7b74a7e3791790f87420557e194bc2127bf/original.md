Arguments:

  * `old_layout::ImageLayout`
  * `new_layout::ImageLayout`
  * `src_queue_family_index::UInt32`
  * `dst_queue_family_index::UInt32`
  * `image::Image`
  * `subresource_range::ImageSubresourceRange`
  * `next::Any`: defaults to `C_NULL`
  * `src_stage_mask::UInt64`: defaults to `0`
  * `src_access_mask::UInt64`: defaults to `0`
  * `dst_stage_mask::UInt64`: defaults to `0`
  * `dst_access_mask::UInt64`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageMemoryBarrier2.html)

```julia
ImageMemoryBarrier2(
    old_layout::Vulkan.ImageLayout,
    new_layout::Vulkan.ImageLayout,
    src_queue_family_index::Integer,
    dst_queue_family_index::Integer,
    image::Vulkan.Image,
    subresource_range::Vulkan.ImageSubresourceRange;
    next,
    src_stage_mask,
    src_access_mask,
    dst_stage_mask,
    dst_access_mask
) -> Vulkan.ImageMemoryBarrier2

```
