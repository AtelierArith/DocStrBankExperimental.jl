Extension: VK_KHR_swapchain

Arguments:

  * `present_mask::NTuple{Int(VK_MAX_DEVICE_GROUP_SIZE), UInt32}`
  * `modes::DeviceGroupPresentModeFlagKHR`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupPresentCapabilitiesKHR.html)

```julia
_DeviceGroupPresentCapabilitiesKHR(
    present_mask::NTuple{32, UInt32},
    modes::Vulkan.DeviceGroupPresentModeFlagKHR;
    next
) -> Vulkan._DeviceGroupPresentCapabilitiesKHR

```
