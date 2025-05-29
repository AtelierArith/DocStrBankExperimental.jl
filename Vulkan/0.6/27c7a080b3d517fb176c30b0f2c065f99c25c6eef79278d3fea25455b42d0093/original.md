Arguments:

  * `physical_devices::Vector{PhysicalDevice}`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupDeviceCreateInfo.html)

```julia
_DeviceGroupDeviceCreateInfo(
    physical_devices::AbstractArray;
    next
) -> Vulkan._DeviceGroupDeviceCreateInfo

```
