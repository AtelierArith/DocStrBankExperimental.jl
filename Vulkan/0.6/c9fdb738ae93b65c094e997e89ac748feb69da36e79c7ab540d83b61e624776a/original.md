Extension: VK_EXT_swapchain_maintenance1

Arguments:

  * `present_modes::Vector{PresentModeKHR}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainPresentModesCreateInfoEXT.html)

```julia
SwapchainPresentModesCreateInfoEXT(
    present_modes::AbstractArray;
    next
) -> Vulkan.SwapchainPresentModesCreateInfoEXT

```
