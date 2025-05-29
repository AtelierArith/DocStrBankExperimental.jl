Arguments:

  * `private_data_slot_request_count::UInt32`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkDevicePrivateDataCreateInfo.html)

```julia
_DevicePrivateDataCreateInfo(
    private_data_slot_request_count::Integer;
    next
) -> Vulkan._DevicePrivateDataCreateInfo

```
