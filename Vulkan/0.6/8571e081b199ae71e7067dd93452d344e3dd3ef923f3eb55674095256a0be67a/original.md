Arguments:

  * `api_version::VersionNumber`
  * `driver_version::VersionNumber`
  * `vendor_id::UInt32`
  * `device_id::UInt32`
  * `device_type::PhysicalDeviceType`
  * `device_name::String`
  * `pipeline_cache_uuid::NTuple{Int(VK_UUID_SIZE), UInt8}`
  * `limits::_PhysicalDeviceLimits`
  * `sparse_properties::_PhysicalDeviceSparseProperties`

[API documentation](https://www.khronos.org/registry/vulkan/specs/1.3-extensions/man/html/VkPhysicalDeviceProperties.html)

```julia
_PhysicalDeviceProperties(
    api_version::VersionNumber,
    driver_version::VersionNumber,
    vendor_id::Integer,
    device_id::Integer,
    device_type::Vulkan.PhysicalDeviceType,
    device_name::AbstractString,
    pipeline_cache_uuid::NTuple{16, UInt8},
    limits::Vulkan._PhysicalDeviceLimits,
    sparse_properties::Vulkan._PhysicalDeviceSparseProperties
)

```
