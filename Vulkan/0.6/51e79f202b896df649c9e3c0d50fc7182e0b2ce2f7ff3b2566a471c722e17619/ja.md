拡張: VK*EXT*buffer*device*address

引数:

  * `device_address::UInt64`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkBufferDeviceAddressCreateInfoEXT.html)

```julia
_BufferDeviceAddressCreateInfoEXT(
    device_address::Integer;
    next
) -> Vulkan._BufferDeviceAddressCreateInfoEXT

```
