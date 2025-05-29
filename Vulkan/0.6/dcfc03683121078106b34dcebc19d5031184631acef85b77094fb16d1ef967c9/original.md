Extension: VK_KHR_video_queue

Arguments:

  * `flags::VideoCapabilityFlagKHR`
  * `min_bitstream_buffer_offset_alignment::UInt64`
  * `min_bitstream_buffer_size_alignment::UInt64`
  * `picture_access_granularity::Extent2D`
  * `min_coded_extent::Extent2D`
  * `max_coded_extent::Extent2D`
  * `max_dpb_slots::UInt32`
  * `max_active_reference_pictures::UInt32`
  * `std_header_version::ExtensionProperties`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoCapabilitiesKHR.html)

```julia
VideoCapabilitiesKHR(
    flags::Vulkan.VideoCapabilityFlagKHR,
    min_bitstream_buffer_offset_alignment::Integer,
    min_bitstream_buffer_size_alignment::Integer,
    picture_access_granularity::Vulkan.Extent2D,
    min_coded_extent::Vulkan.Extent2D,
    max_coded_extent::Vulkan.Extent2D,
    max_dpb_slots::Integer,
    max_active_reference_pictures::Integer,
    std_header_version::Vulkan.ExtensionProperties;
    next
) -> Vulkan.VideoCapabilitiesKHR

```
