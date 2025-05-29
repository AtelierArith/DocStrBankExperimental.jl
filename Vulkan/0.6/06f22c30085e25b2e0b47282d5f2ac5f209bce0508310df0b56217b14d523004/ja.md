拡張: VK*KHR*get*display*properties2

引数:

  * `display_properties::_DisplayPropertiesKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayProperties2KHR.html)

```julia
_DisplayProperties2KHR(
    display_properties::Vulkan._DisplayPropertiesKHR;
    next
) -> Vulkan._DisplayProperties2KHR

```
