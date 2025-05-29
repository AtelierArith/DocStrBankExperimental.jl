Extension: VK_KHR_display_swapchain

Arguments:

  * `src_rect::_Rect2D`
  * `dst_rect::_Rect2D`
  * `persistent::Bool`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPresentInfoKHR.html)

```julia
_DisplayPresentInfoKHR(
    src_rect::Vulkan._Rect2D,
    dst_rect::Vulkan._Rect2D,
    persistent::Bool;
    next
) -> Vulkan._DisplayPresentInfoKHR

```
