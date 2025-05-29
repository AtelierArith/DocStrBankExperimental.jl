Extension: VK_EXT_swapchain_maintenance1

Arguments:

  * `present_modes::Vector{PresentModeKHR}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainPresentModeInfoEXT.html)

```julia
_SwapchainPresentModeInfoEXT(
    present_modes::AbstractArray;
    next
) -> Vulkan._SwapchainPresentModeInfoEXT

```
