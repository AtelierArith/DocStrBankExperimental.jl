拡張: VK*KHR*video_queue

引数:

  * `device::Device`
  * `queue_family_index::UInt32`
  * `video_profile::_VideoProfileInfoKHR`
  * `picture_format::Format`
  * `max_coded_extent::_Extent2D`
  * `reference_picture_format::Format`
  * `max_dpb_slots::UInt32`
  * `max_active_reference_pictures::UInt32`
  * `std_header_version::_ExtensionProperties`
  * `allocator::_AllocationCallbacks`: デフォルトは `C_NULL`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`
  * `flags::VideoSessionCreateFlagKHR`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/vkCreateVideoSessionKHR.html)

```julia
VideoSessionKHR(
    device,
    queue_family_index::Integer,
    video_profile::Vulkan._VideoProfileInfoKHR,
    picture_format::Vulkan.Format,
    max_coded_extent::Vulkan._Extent2D,
    reference_picture_format::Vulkan.Format,
    max_dpb_slots::Integer,
    max_active_reference_pictures::Integer,
    std_header_version::Vulkan._ExtensionProperties;
    allocator,
    next,
    flags
) -> Vulkan.VideoSessionKHR

```
