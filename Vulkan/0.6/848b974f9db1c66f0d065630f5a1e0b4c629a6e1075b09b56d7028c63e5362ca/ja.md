拡張: VK*KHR*shared*presentable*image

引数:

  * `next::Any`: デフォルトは `C_NULL`
  * `shared_present_supported_usage_flags::ImageUsageFlag`: デフォルトは `0`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSharedPresentSurfaceCapabilitiesKHR.html)

```julia
SharedPresentSurfaceCapabilitiesKHR(
;
    next,
    shared_present_supported_usage_flags
) -> Vulkan.SharedPresentSurfaceCapabilitiesKHR

```
