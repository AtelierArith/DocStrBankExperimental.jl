拡張: VK*KHR*video_queue

戻りコード:

  * `SUCCESS`
  * `ERROR_OUT_OF_HOST_MEMORY`
  * `ERROR_OUT_OF_DEVICE_MEMORY`
  * `ERROR_INITIALIZATION_FAILED`
  * `ERROR_VIDEO_STD_VERSION_NOT_SUPPORTED_KHR`

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
_create_video_session_khr(
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
) -> ResultTypes.Result{Vulkan.VideoSessionKHR, Vulkan.VulkanError}

```
