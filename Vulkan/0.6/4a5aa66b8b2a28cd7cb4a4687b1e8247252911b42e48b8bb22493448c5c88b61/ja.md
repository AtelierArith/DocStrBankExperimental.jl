拡張: VK*KHR*swapchain

引数:

  * `device_masks::Vector{UInt32}`
  * `mode::DeviceGroupPresentModeFlagKHR`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupPresentInfoKHR.html)

```julia
DeviceGroupPresentInfoKHR(
    device_masks::AbstractArray,
    mode::Vulkan.DeviceGroupPresentModeFlagKHR;
    next
) -> Vulkan.DeviceGroupPresentInfoKHR

```
