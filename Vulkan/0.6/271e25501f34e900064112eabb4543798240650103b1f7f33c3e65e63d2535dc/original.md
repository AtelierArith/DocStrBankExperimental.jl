Extension: VK_KHR_swapchain

Arguments:

  * `modes::DeviceGroupPresentModeFlagKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupSwapchainCreateInfoKHR.html)

```julia
_DeviceGroupSwapchainCreateInfoKHR(
    modes::Vulkan.DeviceGroupPresentModeFlagKHR;
    next
) -> Vulkan._DeviceGroupSwapchainCreateInfoKHR

```
