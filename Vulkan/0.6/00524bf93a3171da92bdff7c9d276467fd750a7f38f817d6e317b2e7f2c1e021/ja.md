拡張機能: VK*KHR*get*display*properties2

引数:

  * `capabilities::_DisplayPlaneCapabilitiesKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPlaneCapabilities2KHR.html)

```julia
_DisplayPlaneCapabilities2KHR(
    capabilities::Vulkan._DisplayPlaneCapabilitiesKHR;
    next
) -> Vulkan._DisplayPlaneCapabilities2KHR

```
