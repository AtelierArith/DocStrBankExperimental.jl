拡張: VK*KHR*swapchain

引数:

  * `swapchain::SwapchainKHR` (externsync)
  * `image_index::UInt32`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindImageMemorySwapchainInfoKHR.html)

```julia
BindImageMemorySwapchainInfoKHR(
    swapchain::Vulkan.SwapchainKHR,
    image_index::Integer;
    next
) -> Vulkan.BindImageMemorySwapchainInfoKHR

```
