拡張: VK*KHR*get*display*properties2

引数:

  * `display_plane_properties::_DisplayPlanePropertiesKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPlaneProperties2KHR.html)

```julia
_DisplayPlaneProperties2KHR(
    display_plane_properties::Vulkan._DisplayPlanePropertiesKHR;
    next
) -> Vulkan._DisplayPlaneProperties2KHR

```
