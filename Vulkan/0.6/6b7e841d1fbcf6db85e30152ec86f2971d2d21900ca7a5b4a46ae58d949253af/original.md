Extension: VK_KHR_swapchain

Arguments:

  * `swapchain::SwapchainKHR` (externsync)
  * `timeout::UInt64`
  * `device_mask::UInt32`
  * `next::Any`: defaults to `C_NULL`
  * `semaphore::Semaphore`: defaults to `C_NULL` (externsync)
  * `fence::Fence`: defaults to `C_NULL` (externsync)

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkAcquireNextImageInfoKHR.html)

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
