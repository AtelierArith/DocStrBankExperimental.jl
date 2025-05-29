引数:

  * `src_access_mask::AccessFlag`
  * `dst_access_mask::AccessFlag`
  * `old_layout::ImageLayout`
  * `new_layout::ImageLayout`
  * `src_queue_family_index::UInt32`
  * `dst_queue_family_index::UInt32`
  * `image::Image`
  * `subresource_range::_ImageSubresourceRange`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkImageMemoryBarrier.html)

```julia
_ImageMemoryBarrier(
    src_access_mask::Vulkan.AccessFlag,
    dst_access_mask::Vulkan.AccessFlag,
    old_layout::Vulkan.ImageLayout,
    new_layout::Vulkan.ImageLayout,
    src_queue_family_index::Integer,
    dst_queue_family_index::Integer,
    image,
    subresource_range::Vulkan._ImageSubresourceRange;
    next
) -> Vulkan._ImageMemoryBarrier

```
