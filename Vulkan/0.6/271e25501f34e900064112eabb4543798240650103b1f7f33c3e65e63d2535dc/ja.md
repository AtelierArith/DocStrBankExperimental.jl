拡張: VK*KHR*swapchain

引数:

  * `modes::DeviceGroupPresentModeFlagKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupSwapchainCreateInfoKHR.html)

```julia
_DeviceGroupSwapchainCreateInfoKHR(
    modes::Vulkan.DeviceGroupPresentModeFlagKHR;
    next
) -> Vulkan._DeviceGroupSwapchainCreateInfoKHR

```
