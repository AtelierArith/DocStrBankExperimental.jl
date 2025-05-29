Extension: VK_KHR_video_queue

Arguments:

  * `image_usage::ImageUsageFlag`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceVideoFormatInfoKHR.html)

```julia
_PhysicalDeviceVideoFormatInfoKHR(
    image_usage::Vulkan.ImageUsageFlag;
    next
) -> Vulkan._PhysicalDeviceVideoFormatInfoKHR

```
