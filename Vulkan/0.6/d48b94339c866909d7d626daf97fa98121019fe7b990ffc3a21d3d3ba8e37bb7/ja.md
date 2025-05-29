引数:

  * `physical_devices::Vector{PhysicalDevice}`
  * `next::Any`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupDeviceCreateInfo.html)

```julia
DeviceGroupDeviceCreateInfo(
    physical_devices::AbstractArray;
    next
) -> Vulkan.DeviceGroupDeviceCreateInfo

```
