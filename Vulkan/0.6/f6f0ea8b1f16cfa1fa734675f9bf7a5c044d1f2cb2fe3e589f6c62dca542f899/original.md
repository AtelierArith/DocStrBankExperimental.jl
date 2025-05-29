Extension: VK_KHR_display_swapchain

Arguments:

  * `src_rect::Rect2D`
  * `dst_rect::Rect2D`
  * `persistent::Bool`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDisplayPresentInfoKHR.html)

```julia
DisplayPresentInfoKHR(
    src_rect::Vulkan.Rect2D,
    dst_rect::Vulkan.Rect2D,
    persistent::Bool;
    next
) -> Vulkan.DisplayPresentInfoKHR

```
