引数:

  * `device_uuid::NTuple{Int(VK_UUID_SIZE), UInt8}`
  * `driver_uuid::NTuple{Int(VK_UUID_SIZE), UInt8}`
  * `device_luid::NTuple{Int(VK_LUID_SIZE), UInt8}`
  * `device_node_mask::UInt32`
  * `device_luid_valid::Bool`
  * `next::Ptr{Cvoid}`: デフォルトは `C_NULL`

[API ドキュメント](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceIDProperties.html)

```julia
_PhysicalDeviceIDProperties(
    device_uuid::NTuple{16, UInt8},
    driver_uuid::NTuple{16, UInt8},
    device_luid::NTuple{8, UInt8},
    device_node_mask::Integer,
    device_luid_valid::Bool;
    next
) -> Vulkan._PhysicalDeviceIDProperties

```
