引数:

  * `physical_devices::Vector{PhysicalDevice}`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDeviceGroupDeviceCreateInfo.html)

```julia
_DeviceGroupDeviceCreateInfo(
    physical_devices::AbstractArray;
    next
) -> Vulkan._DeviceGroupDeviceCreateInfo

```
