Extension: VK_KHR_swapchain

Arguments:

  * `swapchain::SwapchainKHR` (externsync)
  * `image_index::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindImageMemorySwapchainInfoKHR.html)

```julia
_BindImageMemorySwapchainInfoKHR(
    swapchain,
    image_index::Integer;
    next
) -> Vulkan._BindImageMemorySwapchainInfoKHR

```
