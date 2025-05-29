拡張: VK*KHR*video_queue

引数:

  * `image_usage::ImageUsageFlag`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceVideoFormatInfoKHR.html)

```julia
_PhysicalDeviceVideoFormatInfoKHR(
    image_usage::Vulkan.ImageUsageFlag;
    next
) -> Vulkan._PhysicalDeviceVideoFormatInfoKHR

```
