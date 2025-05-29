拡張: VK*KHR*display_swapchain

引数:

  * `src_rect::_Rect2D`
  * `dst_rect::_Rect2D`
  * `persistent::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPresentInfoKHR.html)

```julia
_DisplayPresentInfoKHR(
    src_rect::Vulkan._Rect2D,
    dst_rect::Vulkan._Rect2D,
    persistent::Bool;
    next
) -> Vulkan._DisplayPresentInfoKHR

```
