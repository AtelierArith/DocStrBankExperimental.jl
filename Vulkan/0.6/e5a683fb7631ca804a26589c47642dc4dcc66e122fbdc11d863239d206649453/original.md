Extension: VK_EXT_swapchain_maintenance1

Arguments:

  * `fences::Vector{Fence}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkSwapchainPresentFenceInfoEXT.html)

```julia
_SwapchainPresentFenceInfoEXT(
    fences::AbstractArray;
    next
) -> Vulkan._SwapchainPresentFenceInfoEXT

```
