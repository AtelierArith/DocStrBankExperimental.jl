Extension: VK_EXT_swapchain_maintenance1

Arguments:

  * `fences::Vector{Fence}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainPresentFenceInfoEXT.html)

```julia
SwapchainPresentFenceInfoEXT(
    fences::AbstractArray;
    next
) -> Vulkan.SwapchainPresentFenceInfoEXT

```
