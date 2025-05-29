拡張: VK*EXT*swapchain_maintenance1

引数:

  * `present_modes::Vector{PresentModeKHR}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainPresentModesCreateInfoEXT.html)

```julia
SwapchainPresentModesCreateInfoEXT(
    present_modes::AbstractArray;
    next
) -> Vulkan.SwapchainPresentModesCreateInfoEXT

```
