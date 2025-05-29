拡張: VK*KHR*swapchain

引数:

  * `swapchain::SwapchainKHR` (externsync)
  * `timeout::UInt64`
  * `device_mask::UInt32`
  * `next::Any`: デフォルトは `C_NULL`
  * `semaphore::Semaphore`: デフォルトは `C_NULL` (externsync)
  * `fence::Fence`: デフォルトは `C_NULL` (externsync)

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAcquireNextImageInfoKHR.html)

```julia
AcquireNextImageInfoKHR(
    swapchain::Vulkan.SwapchainKHR,
    timeout::Integer,
    device_mask::Integer;
    next,
    semaphore,
    fence
) -> Vulkan.AcquireNextImageInfoKHR

```
