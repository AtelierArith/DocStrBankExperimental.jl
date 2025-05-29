Extension: VK_KHR_video_decode_queue

Arguments:

  * `flags::VideoDecodeCapabilityFlagKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkVideoDecodeCapabilitiesKHR.html)

```julia
_VideoDecodeCapabilitiesKHR(
    flags::Vulkan.VideoDecodeCapabilityFlagKHR;
    next
) -> Vulkan._VideoDecodeCapabilitiesKHR

```
