拡張: VK*KHR*swapchain

引数:

  * `swapchain::SwapchainKHR` (externsync)
  * `image_index::UInt32`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBindImageMemorySwapchainInfoKHR.html)

```julia
_BindImageMemorySwapchainInfoKHR(
    swapchain,
    image_index::Integer;
    next
) -> Vulkan._BindImageMemorySwapchainInfoKHR

```
