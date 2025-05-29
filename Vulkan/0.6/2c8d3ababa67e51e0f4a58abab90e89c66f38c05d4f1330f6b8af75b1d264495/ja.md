拡張: VK*KHR*swapchain

引数:

  * `present_mask::NTuple{Int(VK_MAX_DEVICE_GROUP_SIZE), UInt32}`
  * `modes::DeviceGroupPresentModeFlagKHR`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupPresentCapabilitiesKHR.html)

```julia
_DeviceGroupPresentCapabilitiesKHR(
    present_mask::NTuple{32, UInt32},
    modes::Vulkan.DeviceGroupPresentModeFlagKHR;
    next
) -> Vulkan._DeviceGroupPresentCapabilitiesKHR

```
