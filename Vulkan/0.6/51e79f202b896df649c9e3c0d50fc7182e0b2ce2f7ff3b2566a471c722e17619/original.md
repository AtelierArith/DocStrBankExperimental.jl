Extension: VK_EXT_buffer_device_address

Arguments:

  * `device_address::UInt64`
  * `next::Ptr{Cvoid}`: defaults to `C_NULL`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferDeviceAddressCreateInfoEXT.html)

```julia
_BufferDeviceAddressCreateInfoEXT(
    device_address::Integer;
    next
) -> Vulkan._BufferDeviceAddressCreateInfoEXT

```
