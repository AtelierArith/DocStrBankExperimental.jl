Extension: VK_KHR_swapchain

Arguments:

  * `device_masks::Vector{UInt32}`
  * `mode::DeviceGroupPresentModeFlagKHR`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupPresentInfoKHR.html)

```julia
DeviceGroupPresentInfoKHR(
    device_masks::AbstractArray,
    mode::Vulkan.DeviceGroupPresentModeFlagKHR;
    next
) -> Vulkan.DeviceGroupPresentInfoKHR

```
