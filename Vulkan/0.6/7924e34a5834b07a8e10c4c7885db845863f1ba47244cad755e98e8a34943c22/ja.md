拡張: VK*KHR*get*display*properties2

引数:

  * `display_mode_properties::_DisplayModePropertiesKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayModeProperties2KHR.html)

```julia
_DisplayModeProperties2KHR(
    display_mode_properties::Vulkan._DisplayModePropertiesKHR;
    next
) -> Vulkan._DisplayModeProperties2KHR

```
