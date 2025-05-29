Arguments:

  * `physical_devices::Vector{PhysicalDevice}`
  * `next::Any`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupDeviceCreateInfo.html)

```julia
DeviceGroupDeviceCreateInfo(
    physical_devices::AbstractArray;
    next
) -> Vulkan.DeviceGroupDeviceCreateInfo

```
