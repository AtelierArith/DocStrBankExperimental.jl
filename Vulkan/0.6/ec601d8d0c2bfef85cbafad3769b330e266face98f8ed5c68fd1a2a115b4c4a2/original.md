Extension: VK_KHR_video_queue

Arguments:

  * `queue_family_index::UInt32`
  * `video_profile::VideoProfileInfoKHR`
  * `picture_format::Format`
  * `max_coded_extent::Extent2D`
  * `reference_picture_format::Format`
  * `max_dpb_slots::UInt32`
  * `max_active_reference_pictures::UInt32`
  * `std_header_version::ExtensionProperties`
  * `next::Any`: defaults to `C_NULL`
  * `flags::VideoSessionCreateFlagKHR`: defaults to `0`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoSessionCreateInfoKHR.html)

```julia
VideoSessionCreateInfoKHR(
    queue_family_index::Integer,
    video_profile::Vulkan.VideoProfileInfoKHR,
    picture_format::Vulkan.Format,
    max_coded_extent::Vulkan.Extent2D,
    reference_picture_format::Vulkan.Format,
    max_dpb_slots::Integer,
    max_active_reference_pictures::Integer,
    std_header_version::Vulkan.ExtensionProperties;
    next,
    flags
) -> Vulkan.VideoSessionCreateInfoKHR

```
