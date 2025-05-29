Extension: VK_KHR_swapchain

Arguments:

  * `swapchain::SwapchainKHR` (externsync)
  * `image_index::UInt32`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindImageMemorySwapchainInfoKHR.html)

```julia
BindImageMemorySwapchainInfoKHR(
    swapchain::Vulkan.SwapchainKHR,
    image_index::Integer;
    next
) -> Vulkan.BindImageMemorySwapchainInfoKHR

```
